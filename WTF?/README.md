# WTF? 250p

### Descripción
```
Querido diario,

Hoy me ha llegado un paquete de alguien desconocido. En él se encontraba 
un medio que contenía información aleatoria, al parecer. Sin embargo, 
investigando un poco más, me he dado cuenta que son instrucciones de una 
arquitectura completamente desconocida. Es muy sofisticada y realmente 
compleja. Me pregunto si los rusos están desarrollando algo 
extraordinario...

Grace Murray Hopper,
24 de Febrero, 1975
```

### Ficheros
*file.exe*

### Pistas
Pista|Coste
---|---|
Seguro que es un .exe?|5p|
abcdefghijklmnoqemutuvwxyz|15p|
---

Según la descripción, tiene toda la pinta de ser un ejecutable. Como 
siempre, lo primero es mirar qué tenemos delante nuestra:

```bash
$ file file.exe 
file.exe: ELF 32-bit MSB executable, MIPS, MIPS-II version 1 (SYSV), 
statically linked, for GNU/Linux 2.6.26, 
BuildID[sha1]=772236cfe645c413aa1458244ae79621f99792c2, stripped
```

Se trata de un ejecutable, pero no el que esperabamos (Windows). 
Máquinas MIPS no son fáciles de encontrar, asi que probamos a buscar el 
flag dentro del binario. Con suerte, está ahi:

```bash
$ strings file.exe  | grep -i codecamp
codecamp18{flAgg_c0mpiler}
```

Bingo!

... O puede que no. Será para hacerte ilusiones, porque la plataforma no 
lo coge. Habrá que ejecutarlo de alguna forma.

Como siempre, Google es mi amigo, asi que encontramos esta url:

[https://people.debian.org/~aurel32/qemu/mips/](https://people.debian.org/~aurel32/qemu/mips/)

Donde al parecer ya hay una máquina preparada para ello. Y por si fuera 
poco, podremos ejecutar nuestro binario ahí (`for GNU/Linux 2.6.26`). 
Por suerte, no había que compilar un kernel de Linux para otra 
arquitectura (aunch!).

Bajamos cualquiera de ellos y lanzamos la máquina QEMU:
```bash
$ qemu-system-mips64 -M malta -kernel vmlinux-3.2.0-4-5kc-malta -hda 
debian_wheezy_mips_standard_codecamp.qcow2 -append "root=/dev/sda1 
console=ttyS0" -nographic -net user,hostfwd=tcp::10022-:22 -net nic
$ qemu-system-mips64 -M malta -kernel vmlinux-3.2.0-4-5kc-malta -hda 
debian_wheezy_mips_standard_codecamp.qcow2 -append "root=/dev/sda1 
console=ttyS0" -nographic -net user,hostfwd=tcp::10022-:22 -net nic
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-4-5kc-malta 
(debian-kernel@lists.debian.org) (gcc version 4.6.3 (Debian 4.6.3-14) ) 
#1 Debian 3.2.51-1
[    0.000000] bootconsole [early0] enabled
[    0.000000] CPU revision is: 000182a0 (MIPS 20Kc)
[    0.000000] FPU revision is: 000f8200
[    0.000000] Checking for the multiply/shift bug... no.
[    0.000000] Checking for the daddiu bug... no.
[    0.000000] Determined physical RAM map:
[    0.000000]  memory: 0000000000001000 @ 0000000000000000 (reserved)
[    0.000000]  memory: 00000000000ef000 @ 0000000000001000 (ROM data)
[    0.000000]  memory: 0000000000748000 @ 00000000000f0000 (reserved)
[    0.000000]  memory: 00000000077c7000 @ 0000000000838000 (usable)
[    0.000000] Wasting 117824 bytes for tracking 2104 unused pages
...
```
Esperamos a que termine y entramos en la shell con `root:root`. Ahora 
que estamos dentro, verificamos que realmente el entorno es MIPS:
```bash
# uname -a
Linux debian-mips 3.2.0-4-5kc-malta #1 Debian 3.2.51-1 mips64 GNU/Linux
```

Estupendo. Copiamos el binario ahi por ssh:
```bash
$ scp -P 10022 file.exe root@localhost:/root
root@localhost's password: 
file.exe                                      100%  650KB   5.2MB/s   
00:00
```

Y lo ejecutamos desde el entorno virtual:
```bash
# ./file.exe 
codecamp18{flAgg_c0mpiler}
CodeCamp18{Es_mas_facil_pedir_perdon_que_pedir_permiso_:)}
```

Aaamigoooo. Ahí estaba el truco, el formato del flag que vimos 
anteriormente no era el correcto ;)

Asi que ahi está el flag:
`CodeCamp18{Es_mas_facil_pedir_perdon_que_pedir_permiso_:)}`
