# Nuclear_Attack 350p

### Descripción
```
Con la caída del imperio nazi, Enigma siguió la misma suerte. Sin embargo, el equipo detrás de ese invento no se dió por vencido, por lo que huyeron junto con algunos generales a 
Japón, según fuentes de espionaje.

Meses más tarde, se supo que su intención era crear otra máquina criptográfica, aún más potente. EEUU no tardó mucho en reaccionar, con las Top Secret Rosies. Otros paises siguieron 
el mismo camino, en la búsqueda de mayor capacidad de cómputo...

Recientemente, aquel grupo ha vuelto a la acción. Y esta vez se han asegurado de no ser interceptados sus canales de comunicación. Hemos conseguido capturar un correo electrónico que 
podría ser la clave para desactivar un ataque nuclear no muy lejano, pero necesitamos tu ayuda. ¿Eres capaz de descubrir la contraseña para desactivarlo?
```

### Ficheros
*file.exe*

### Pistas
Pista|Coste
---|---|
PGP/MIME... Habrá que buscar su clave pública en los keyservers?|5p|
Factorizar su módulo... o ya lo habrá hecho alguien?|15p|
---

Como siempre, a ver que tenemos:

```bash
$ file mail.exe 
mail.exe: LZMA compressed data, streamed
```

Extraemos:

```bash
$ 7z e mail.exe 

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=es_ES.utf8,Utf16=on,HugeFiles=on,64 bits,4 CPUs Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz (306D4),ASM,AES-NI)

Scanning the drive for archives:
1 file, 2311 bytes (3 KiB)

Extracting archive: mail.exe
WARNING:
mail.exe
Can not open the file as [PE] archive
The file is open as [lzma] archive

--
Path = mail.exe
Open WARNING: Can not open the file as [PE] archive
Type = lzma

Everything is Ok

Archives with Warnings: 1
Size:       3232
Compressed: 2311
$ ls
mail  mail.exe
$ file mail
mail: SMTP mail, ASCII text
```

Uhh, un correo:

```
$ cat mail
Return-Path: <president@evilcorp.com>
Received: from ?IPv6:2a01:e35:87cd:db90:5554:9ecc:3e80:fa36? ([2a01:e35:87cd:db90:5554:9ecc:3e80:fa36])
        by smtp.norte.gov with ESMTPSA id x65sm6843301wmg.29.2018.02.13.03.18.40
        for <corea@norte.gov>
        Tue, 13 Feb 1990 13:18:40 -0800 (PST)
To: corea@norte.gov
From: President <president@evilcorp.com>
Subject: =?UTF-8?Q?C=c3=b3digos_Nucleares?=
Message-ID: <653d2bdc-e445-f229-3655-095707f71d26@norte.gov>
Date: Tue, 13 Feb 1990 12:18:39 +0100
User-Agent: Mozilla/0.01 (X11; Linux x86; rv:2.0)
MIME-Version: 1.0
Content-Type: multipart/encrypted;
 protocol="application/pgp-encrypted";
 boundary="gpmMfCvPcFqg6TkRHicnimsIbNUnb9OEw"

This is an OpenPGP/MIME encrypted message (RFC 4880 and 3156)
--gpmMfCvPcFqg6TkRHicnimsIbNUnb9OEw
Content-Type: application/pgp-encrypted
Content-Description: PGP/MIME version identification

Version: 1

--gpmMfCvPcFqg6TkRHicnimsIbNUnb9OEw
Content-Type: application/octet-stream; name="encrypted.asc"
Content-Description: OpenPGP encrypted message
Content-Disposition: inline; filename="encrypted.asc"

-----BEGIN PGP MESSAGE-----

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
gCq9DMc8enwUD4ZolA==
=au1Z
-----END PGP MESSAGE-----

--gpmMfCvPcFqg6TkRHicnimsIbNUnb9OEw--
```

Está dificil la cosa cuando lo han encriptado, pero por probar no se pierde nada. Probamos a obtener la clave pública del destinatario:
```bash
$ gpg --keyserver pgp.mit.edu --search corea@norte.gov
gpg: error searching keyserver: No data
gpg: búsqueda del servidor de claves fallida: No data
```

Que raro, si las fechas que se mencionan en el correo son correctas, una clave pública tan antigua debería estar hasta en la sopa. Busquemos el otro correo...

```bash
$ gpg --keyserver pgp.mit.edu --search president@evilcorp.com
gpg: data source: http://pgp.mit.edu:11371
(1)	President <president@evilcorp.com>
	  5831 bit RSA key B0689CEF7A225189, creado: 1990-02-13
```

Ya lo tenemos. O hay algún error, o no este no sabía usar la encriptación de los emails correctamente. A pesar de ello, la clave es de 5831 bits, que no es poco. Crackearlo es 
impensable, ni hace 20 años, ni ahora. Realmente se han asegurado de protegerlo bien.

Sin embargo, existen numerosos proyectos en internet que utilizan de forma conjunta equipos (ya en aquella época) para buscar números primos y demás. ¿Y si...?

Como siempre, Google (o Bing?) es tu amigo. Buscando buscando, hay algo interesante: [factorDB](https://factordb.com)

Entendiendo un poco RSA, sabemos que la clave pública no es más que el módulo (la multiplicación de dos números primos `p` y `q`) y un exponente. Vamos a extraer dicho módulo de la 
clave pública:

```bash
$ gpg --keyserver pgp.mit.edu --search president@evilcorp.com
gpg: data source: http://pgp.mit.edu:11371
(1)	President <president@evilcorp.com>
	  5831 bit RSA key B0689CEF7A225189, creado: 1990-02-13
Keys 1-1 of 1 for "president@evilcorp.com".  Introduzca número(s), O)tro, o F)in >1
gpg: clave B0689CEF7A225189: clave pública "President <president@evilcorp.com>" importada
gpg: Cantidad total procesada: 1
gpg:               importadas: 1
$ gpg --list-keys --with-key-data president@evilcorp.com
tru::1:1518518927:0:3:1:5
pub:-:5831:1:B0689CEF7A225189:634906040:::-:::escaESCA:::::::1519929535:1 http\x3a//pgp.mit.edu\x3a11371:
fpr:::::::::FDAC3716D12EC60B13D32E86B0689CEF7A225189:
grp:::::::::E1077748EB6202B1FC78000BFCE08196503A66AB:
pkd:0:5831:4AFA685B041E1B1BA95C3A86D2B41BBCC2DD0A0FF90A5748C80B0137A63C6352922149ECEABC92642429642B7E9E73E6809785E9CC34F583D90ED4A342A80D46C77FF365565D0C6F5D043B87C6363374747180229D0BCC94581D26EE5C6C4A15AB97BEF45A374944E586D255FD1A288B70C841197D4131E4F7996783C68CEA20C4C844B76840B04385C2E9DF55C55D80D1ACF130ED6A44881F98CA234A889E5B5351E5B6B704342449D7000439589B8AE92D26D7E144B8195D06F59D022FC02393B307D588EE5B6BCF09A578EB74A754D1C9A05EC1BA1EFB265D7670C4EE82EB89B33104A6E348768B7774BB55027AA80D8FF7534BA23D101A2886D909804AEEAAA3110179CAA5BD9F13A14E359E8D2B38918FB79CBF022A205AAD3EEA0643195147818AFB8BB1CE7CA65C0FF7E026CA1C62217D7F12BD14E54D85A543EB9CBE8D2DA0691E1B69D67BB16DB6AB9B6F6B53C9A38A64BCE8F135939D180DF95FB884AE8B932DA6538A24E7E2E4936E129C395A8D6C7AEF13E444F4355FF7AC35DDC8509D847C9F508679F3EE8FCD12485C79DA949CFC45575FD936B9D55BC66BE267F7976AFACD159D0277D0C0E5A23635AFAC76BC3F4BF9174DD47A58D742A5C7473817DDFC494CC087532926649AFCD333DAC7AA5FA5B54054FE1522D83CE46A909CC1330A1B6E6F215FF73AFE0F1001F6874CB5EA060A0B3041EEC90AA798D55F6D2514F6738194D49CAFCDCA414C48876BC5D2F7E7751D1530EB36A1F4F5DADA67E07007A0B44613616DDE5CF08B0E83393BAD39570EF874684F7FA17E2ACA32A5FFAC04EC95DBC78298DFE6DE90CA78F1BFC17BE601B3380B95CCF9F41C6AFB695825636340C5A21975DE96860A4C400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001:
pkd:1:17:010001:
uid:-::::1518518921::6D56CCCAF9C99883F23CF2120CDE18041E337282::President <president@evilcorp.com>:::::::::1519929535:1:
$ gpg --list-keys --with-key-data president@evilcorp.com | grep pkd:0 | cut -d":" -f4 | xargs -I{} python -c 'print(int("{}", 16))'
1184757578872726401875541948122658312538049254193811194706693679652903378440466755792536161053191231432973156335040510349121778456628168943028766026325269453310699198719079556693102485413885649073042144349442001704335216057511775363148519784811675479570531670763418634378774880394019792620389776531074083392140830437849497447329664549296428813777546855940919082901504207170768426813757805483319503728328687467699567371168782338826298888423104758901089557046371665629255777197328691825066749074347103563098441361558833400318385188377678083115037778182654607468940072820501076215527837271902427707151244226579090790964814802124666768804586924537209470827885832840263287617652116022064863681106011820233657970964986092799261540575771674176693421056457946384672759579487892764356140012868139174882562700663398653410810939857286089056807943991134484292518274473171647231470366805379774254724269612848224383658855657086251162811678080812135302264683778545807214278668333366983221748107612374568726991332801566415332661851729896598399859186545014999769601615937310266497300349207439222706313193098254004197684614395013043216709335205659801602035088735521560206321305834999363607988482888525092210585343868702766655032190348593070756595867719633492847013620378010952424253098519859359544101947494405255181048550165119679168071637363387551385352023888031983210940358096667928019837327581681936262186049576626435407253113152851511562799379477905913074052917135254673527350886619693800827592241738185465519368503599267554966329609741719839452532720121891782656000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001
```

Esos ceros del final tienen buena pinta. Buscamos a ver... BINGO. Este número está factorizado! Se usa como abreviación para ese tocho el `844!/844#+1`, que representa a esa rista de 
números. Mirando por la web, vemos que está compuesto de los siguientes dos números primos:

- `5054843`
- `(844!/844#+1)/5054843`

Pues nada, tenemos dos números primos, asi que en la práctica tenemos la clave privada del presidente. Ahora toca reconstruirla. Para ello, lo que haremos será crear la clave privada 
con la ayuda de OpenSSL y transformarla en GPG para importartla.

Podemos reconstruir la clave manualmente, mediante la ayuda de OpenSSL tal como explican 
[aqui](https://stackoverflow.com/questions/19850283/how-to-generate-rsa-keys-using-specific-input-numbers-in-openssl), o usar herramientas que nos automatizan el proceso, como es el 
caso de [rsatool](https://github.com/ius/rsatool)

```bash
$ python ./rsatool.py -p 5054843 -q 
234380687762750772254557055109853720983628819766273887182389973269773834408005699839250429944746301998493950521319952043836332494724004077481489736936492281424111332185604885590532185750157947353269358583331272940491963065422956828362131085933168543428654791209819698530453840088410222161279742324553716780549035932045663425615724276559416150764236763820541821556377558545491606131735012439223038920957324978777692476535627780887813704287770116480588923740336082768397708335813534035590571076954735006230350054701764901564378001132315698650786538411312598129939955171802779278313458453982137072734255886202418312688408878796961007256721311529796171874751764365433958605173714796298295254888433096781375399980768164866695472159228619796241628287259949791649861247814797168647204277732886891814951067849861737231168394321502386732250228937107341274994747507127649114219841606431648669350219109247947836096760207406293561009051731342028882452864268691590859355803599313961525956020318014737297872818760457330788050558984699742088895577280049053901298540021383506173643840017867859141483364191183386743699975329602332499092322987214400447656848834973026898426183728159185875404732231747868768740264310623053308486967913463003847319465257305418357605492470886029976450920141309900138164913825099069383766924148805349477337206588490988025810499730265011833392324568076185159427766120863088381218971504481234215830860256758026226096315845597165544815717745388862429031106726696318921792871062105285074010904710446507431848943625295551108616572289563055203890605504463739032053023209622929930761449959969083114945409778305676358296390214295478613282351202599170735866573897547362005110742311877935674757851035136007191519103560684278423682001597280073782707 
-o privatekey.pem
Using (p, q) to initialise RSA instance

n =
4afa685b041e1b1ba95c3a86d2b41bbcc2dd0a0ff90a5748c80b0137a63c6352922149eceabc9264
2429642b7e9e73e6809785e9cc34f583d90ed4a342a80d46c77ff365565d0c6f5d043b87c6363374
747180229d0bcc94581d26ee5c6c4a15ab97bef45a374944e586d255fd1a288b70c841197d4131e4
f7996783c68cea20c4c844b76840b04385c2e9df55c55d80d1acf130ed6a44881f98ca234a889e5b
5351e5b6b704342449d7000439589b8ae92d26d7e144b8195d06f59d022fc02393b307d588ee5b6b
cf09a578eb74a754d1c9a05ec1ba1efb265d7670c4ee82eb89b33104a6e348768b7774bb55027aa8
0d8ff7534ba23d101a2886d909804aeeaaa3110179caa5bd9f13a14e359e8d2b38918fb79cbf022a
205aad3eea0643195147818afb8bb1ce7ca65c0ff7e026ca1c62217d7f12bd14e54d85a543eb9cbe
8d2da0691e1b69d67bb16db6ab9b6f6b53c9a38a64bce8f135939d180df95fb884ae8b932da6538a
24e7e2e4936e129c395a8d6c7aef13e444f4355ff7ac35ddc8509d847c9f508679f3ee8fcd12485c
79da949cfc45575fd936b9d55bc66be267f7976afacd159d0277d0c0e5a23635afac76bc3f4bf917
4dd47a58d742a5c7473817ddfc494cc087532926649afcd333dac7aa5fa5b54054fe1522d83ce46a
909cc1330a1b6e6f215ff73afe0f1001f6874cb5ea060a0b3041eec90aa798d55f6d2514f6738194
d49cafcdca414c48876bc5d2f7e7751d1530eb36a1f4f5dada67e07007a0b44613616dde5cf08b0e
83393bad39570ef874684f7fa17e2aca32a5ffac04ec95dbc78298dfe6de90ca78f1bfc17be601b3
380b95ccf9f41c6afb695825636340c5a21975de96860a4c40000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000
000000000000000001

e = 65537 (0x10001)

d =
48f785d3169eb4509e371773db908c1a530051a05c569f5cc12d8d472d6aec9ff5276f16ef6ab6d9
d1a2c8dc704990b9310a245de7ad08b9a22b9f78a4b8118143dcabe0d85baf5188cae1336922a8b8
774c87664b8e06a55a192a7ae693b3b08f4670d257f3569a9ac892cb8aa00334919168aa3251393c
5891a06dc5555f6664fb8eec87135620c560cc2f5709ae8a5479ed7783767de8d1023200939db9a4
129960427425bdcf0dc962bd04a4232eedef66c730cd466e33e0ca3913f1b8d83a8270c8e6bc05cb
c781678cb4fc2d56ceaf9ad5666fcf635fa20818baf4664884e19b9c10b8559f7bdac18c17f6bbb1
817cd80a6f7fe61ef3d917940133ed0f0b638655cb1cdb56bab3658e87ddade734c01e323d8b5ec6
25798cb3a4eeec42dab7c0a057c116c62b5ec41a4949585b302271bcb1f89ada72ec8e6d33d586a5
1b46e63ec094694e06088b261de40d69af9d537a8ac1c5e3f0045da39b0434cbeee98cff8be1d9e4
bd1ae2a8dd589abe2730e97f50cde6dbef6d05ae0ae99c495c101b57d0b380992a1d5b9dcbd329c6
7c9947846980ae96f8545fa63fac8335904d409e1cb949fe4c0e5e716cf83864ca5d052c153bfe3b
727d8e1d0d9509b06392f97bfaab493b25c58e3e469c76f4593cccccb38bf1e2db75bbbcf76bf41c
b4d7e95bb4953d022dfb9e0b5e04993175f7b0e5e9fa1d5395c8f8e9c72d9d745672cc6c9321d448
e8b288801267442d3551f3b3c301eb5afe488b58425f276fe792d5d3c9598861f9a2f09233140e57
45909b6987322fb2eff202bfa3f599586afe1f7617d82f036e6fa14fa55b5720ca1d033ae39bb7ff
a52e7e46161af337e5accaab97c7b5bdac1fd8112e175e55531a11a8a52868da154f9aed139fb3d0
2d730174a37590513f7536dbe2bc2ae75b4e4648ac1882816c1874664f145b5cfcbae752ce675524
403b1955fecf27ca5c153248ae1e479b6bebac7140a8a3e352a1942ddabe51586f1979237b6c1a25
4ae8643efeb7cc28fd

p = 5054843 (0x4d217b)

q =
f8daf7e4ea66be4f027433189f840a3887335eb07da761879b4544c5d3c0f85fe032f17f5e0ad0d4
dcb5bfd2ecedf0ad65bdd350f6d241e6809a9bfc3c7e8b4c8aa73c92dfd6dc0fd595eaab332c60e7
886fefe1c6702dcc9b5fcde4b39675b437e1ebfdf30324eacfdc1e39a016b92d639af397bc5d1f35
dd9f6f4f34ba62f78cb42ad92a20f897b96420e2096c35490233cc52201cd2bdde4f7b4685b1df63
f65d7558b784b9b57519ab09743228b8b983451d966e160c1038c2808c2e4539ebf54f440044a7b4
35f65fb43952075e9c6dba6716dd9067555281084c05bc5b6f1712d88eafadbff6d2ce04f3fb81b1
d92cf350e665f6c1d6d076e73a65f52183746d2cc2b6fea920f9be65f9547fefcebfccfcc9b55ca9
b363cb702df0d80925932cf0f5aa666bc2a7de6933605c09cdca72c24575d6806cac3fecee42b26f
64075b1a108ad4c201885e6a519510a4c5fc8136945850bb6927f0c6e78ed1a27e61047af82c0f5d
125fbfe82c349ae557a9c23b70dea61a346d3f82a0a55e4d0a397505f81c23898f72319abb274712
1884134feb057a2cc69e49242b1f88a50a1a92be7d78f8773796d6c69bb93a39225bb4e1a3ea2865
b490140371b4a5c4891a90d9ee09aa033943426224c47722bdf4b30c607f689b0922a086b2b0ac2c
d523b42a17aa1469a961a075b2d64dfc7cb68fd0535a6ed64716a89703f12416ce9e18b2edc71981
44cd28e538b65ed70a6ac105f755788d38bcaefabf5fcca7b50d2a64894ecb492f74db70ce029eb6
2cd48773333c3085eb7d0ac161bc5b9892315d50b27dafddd2d79190d5a45cf11b4a6de09cc3c150
9b810827a94d3c3c343acc5fb9b1482516208bc7416d48651b34e915b78ea44d6aa66b67b6f15318
66d4d89ef421c550eb452168a7c122eb105cec952198fd20cb4fe8c6269ef9303211ead52d8403b3
d83ae71d9cb8c07273a3407bd847de2757138721e7bcf7048abd48f18b06bb4b363ebd01a2d585c8
0671402f95b3

Saving PEM as privatekey.pem
$ pem2openpgp president@evilcorp.com < privatekey.pem | gpg --import
gpg: clave 6940E6CCA101BD5B: clave pública "president@evilcorp.com" importada
gpg: clave 6940E6CCA101BD5B: clave secreta importada
gpg: Cantidad total procesada: 1
gpg:               importadas: 1
gpg:      claves secretas leídas: 1
gpg:  claves secretas importadas: 1
```

Vamos a probar si ha funcionado:

```bash
$ gpg --decrypt mail
gpg: cifrado con clave RSA de 5831 bits, ID B0689CEF7A225189, creada el 1990-02-13
      "President <president@evilcorp.com>"
Content-Type: multipart/mixed; boundary="W5HxWPphg9lpLyU81gZsVXMp9uubu1m7Y";
 protected-headers="v1"
From: president@evilcorp.com>
To: core@norte.gov
Message-ID: <653d2bdc-e445-f229-3655-095707f71d26@norte.gov>
Subject: =?UTF-8?Q?C=c3=b3digos_Nucleares?=

--W5HxWPphg9lpLyU81gZsVXMp9uubu1m7Y
Content-Type: multipart/mixed; boundary="TwrI0XH2dnckRyvxxZ6IqvUhdTVA9rIhI"

--TwrI0XH2dnckRyvxxZ6IqvUhdTVA9rIhI
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: quoted-printable
Content-Language: es-ES

Buenas,


Tal c=C3=B3mo hemos planeado, en unos 28 a=C3=B1os lanzaremos el misil nu=
clear a
la Facultad de Inform=C3=A1tica de la Universidad de Murcia. Esta vez no 
habr=C3=A1 ning=C3=BAn ENIAC con las "Refrigerator Laddies" que=
 impida la conquista del mundo, te lo aseguro. Como ya te dije, este 
canal =
es seguro ahora, y dentro de 90 a=C3=B1os
 


El c=C3=B3digo de acceso es el siguiente:
CodeCamp18{@ra98QKEh*xkw*fbzhru+Qx9*YThV@h$g=3DJRXjLCCTD*fsh8xKC5bF*JFK_$=
%u&fJ6bD#}


Un saludo,

Presidente de EvilCorp


--TwrI0XH2dnckRyvxxZ6IqvUhdTVA9rIhI--

--W5HxWPphg9lpLyU81gZsVXMp9uubu1m7Y--
```

Ahi está nuestro flag:
`CodeCamp18{@ra98QKEh*xkw*fbzhru+Qx9*YThV@h$g=3DJRXjLCCTD*fsh8xKC5bF*JFK_$=%u&fJ6bD#}`