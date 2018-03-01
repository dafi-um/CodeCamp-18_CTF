# Free 150p

### Descripción
```
Corren los años 90, los modems hacen 'beeps' e Internet es algo 
desconocido que no importa mucho a la opinión general. Sin embargo, 
siempre hay alguien al que le importan nuestros derechos en la red...
```

### Ficheros
*Free.exe*

### Pistas
Pista|Coste
---|---|
De METAtags va la cosa...|15p|
Bajar música por P2P está feo...|15p|
¿Quién habrá dicho eso?|15p|
---

Antes de nada, siempre es importante saber que archivo estamos tratando. 
Probamos a averiguarlo:

```bash
$ file Free.exe 
Free.exe: Audio file with ID3 version 2.3.0, contains:MPEG ADTS, layer 
III, v1, 320 kbps, 44.1 kHz, JntStereo
```

Tiene toda la pinta de ser un archivo de música normal y corriente. 
Escuchandolo un poco, vemos que realmente se trata de la canción 
[Dubioza kolektiv "Free.mp3 (The Pirate Bay 
Song)"](https://www.youtube.com/watch?v=GS8-nNhWlw4). Canción que repite 
el mensaje de "Our music is for free, you can download .mp3" ;)

Buscar dentro del mp3 alguna pista o mensaje oculto, no parece dar 
resultados. Sin embargo, los metadatos del archivo tienen algo raro:

```bash
$ exiftool Free.exe 
ExifTool Version Number         : 10.80
File Name                       : Free.exe
Directory                       : .
File Size                       : 8.2 MB
File Modification Date/Time     : 2018:02:28 23:17:48+01:00
File Access Date/Time           : 2018:02:28 23:17:48+01:00
File Inode Change Date/Time     : 2018:02:28 23:17:48+01:00
File Permissions                : rw-r--r--
File Type                       : MP3
File Type Extension             : mp3
MIME Type                       : audio/mpeg
MPEG Audio Version              : 1
Audio Layer                     : 3
Audio Bitrate                   : 320 kbps
Sample Rate                     : 44100
Channel Mode                    : Joint Stereo
MS Stereo                       : Off
Intensity Stereo                : Off
Copyright Flag                  : False
Original Media                  : False
Emphasis                        : None
ID3 Size                        : 312764
XMP Toolkit                     : Adobe XMP Core 5.5-c014 79.151805, 
2013/04/09-12:08:21
Metadata Date                   : 2016:02:02 07:56:36+01:00
Modify Date                     : 2016:02:02 07:56:36+01:00
Instance ID                     : 
xmp.iid:956e6e96-78eb-46f5-8588-38d8f0b0e853
Document ID                     : 
xmp.did:956e6e96-78eb-46f5-8588-38d8f0b0e853
Original Document ID            : 
xmp.did:d5c06e53-6a7b-4c70-a832-f0f6d110fbfb
Format                          : audio/mpeg
Tracks Track Name               : CuePoint Markers, CD Track Markers, 
Subclip Markers
Tracks Track Type               : Cue, Track, InOut
Tracks Frame Rate               : f44100, f44100, f44100
History Action                  : saved, saved
History Instance ID             : 
xmp.iid:d5c06e53-6a7b-4c70-a832-f0f6d110fbfb, 
xmp.iid:956e6e96-78eb-46f5-8588-38d8f0b0e853
History When                    : 2016:02:02 07:56:36+01:00, 2016:02:02 
07:56:36+01:00
History Software Agent          : Adobe Audition CC (Macintosh), Adobe 
Audition CC (Macintosh)
History Changed                 : /metadata, /
Derived From Instance ID        : 
xmp.iid:d5c06e53-6a7b-4c70-a832-f0f6d110fbfb
Derived From Document ID        : 
xmp.did:d5c06e53-6a7b-4c70-a832-f0f6d110fbfb
Derived From Original Document ID: 
xmp.did:d5c06e53-6a7b-4c70-a832-f0f6d110fbfb
Warning                         : [minor] Frame 'TSOA' is not valid for 
this ID3 version
Album Sort Order                : Happy Machine
Performer Sort Order            : Dubioza kolektiv
Title Sort Order                : Free.mp3 (The Pirate Bay Song)
Album Artist Sort Order         : Dubioza kolektiv
Lyrics                          : FREE.MP3..Click it, save it, seed it, 
share it.Link it, stream it - we don’t pay.Click it, save it, seed it, 
share it.Link it, stream it - Pirate Bay .(Let’s get connected)..We do 
file share like we don’t care.Throw music industry in despair.It’s a 
little bit queer but have no fear,.let’s get connected - peer to 
peer..We don’t give a shit about a copyright law.we take it from the 
rich.and give it to the poor.like a high speed internet Robin 
Hoods.pirate gang of file Share-wood..You can find anything if you 
seek.Government secrets from WikiLeaks.Images of naked celebrities.And 
Jamie Oliver’s recipes..It doesn’t really matter.where you’re coming 
from.From Barack Obama to Kim Dotcom.Everybody downloads pornography.And 
Dubioza kolektiv MP3s..Our music is for free.You can download MP3.Keep 
it playing on repeat.If you hate it press delete..This MP3 is for 
free.download now ASAP.once you hear it you will see .It’s mega-hit, 
OMG..Get instructional video of how to start.Doing living-room surgeries 
on open heart .Blueprints of NASA satellites.And stolen numbers of 
credit cards..If you wanna new album.from Rolling Stones.entire season 
of Game of Thrones.it’s a little bit illegal but that’s OK.let’s do it 
like they do on The Pirate Bay
Title                           : Free.mp3 (The Pirate Bay Song)
Artist                          : Dubioza kolektiv
Band                            : Dubioza kolektiv
Album                           : Happy Machine
Year                            : 2016
Track                           : 03/10
User Defined URL                : 
urn:btih:61502e603e5d246d90892a788b91240f7c822be0
Picture MIME Type               : image/jpeg
Picture Type                    : Other
Picture Description             : 
Picture                         : (Binary data 304121 bytes, use -b 
option to extract)
Date/Time Original              : 2016
Duration                        : 0:03:27 (approx)
```

El campo *User Defined URL* tiene buena pinta, y buscando en google 
**urn:btih**, nos encontramos con referencias a links magnet de torrent. 
Probamos a construir un link magnet válido, quedando así:

`magnet:?xt=urn:btih:61502e603e5d246d90892a788b91240f7c822be0`

Efectivamente, descargamos 2 archivos:

```bash
$ file exe.zip password.exe 
exe.zip:      Zip archive data, at least v5.1 to extract
password.exe: ASCII text
$ 7z l exe.zip 

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=es_ES.utf8,Utf16=on,HugeFiles=on,64 bits,4 
CPUs Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz (306D4),ASM,AES-NI)

Scanning the drive for archives:
1 file, 297 bytes (1 KiB)

Listing archive: exe.zip

--
Path = exe.zip
Type = zip
Physical Size = 297

   Date      Time    Attr         Size   Compressed  Name
------------------- ----- ------------ ------------  
------------------------
2018-02-05 16:22:01 .....          124          125  flag.txt
------------------- ----- ------------ ------------  
------------------------
2018-02-05 16:22:01                124          125  1 files
$ cat password.exe 
Girls need modems
```

Uno de ellos es un .zip y el otro un archivo de texto. Al intentar abrir 
el .zip, nos solicita una contraseña. Usando el archvo *password.exe* no 
parece dar resultado, asi que investigamos un poco por itnernet. Hay 
muchos artículos que citan la [misma 
entrevista](https://www.wired.com/1995/02/st-jude/). 

Probando el título del articulo tampoco funciona. Sin embargo, leyendo 
más a fondo la entrevista, caemos en la cuenta de que la descripción del 
reto se asemeja un poco a la entrevistada. Probamos usar su nombre de 
pila como contraseña, sin éxito. Usando su nombre real conseguimos:

```bash
$ 7z e exe.zip 

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=es_ES.utf8,Utf16=on,HugeFiles=on,64 bits,4 
CPUs Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz (306D4),ASM,AES-NI)

Scanning the drive for archives:
1 file, 297 bytes (1 KiB)

Extracting archive: exe.zip
--
Path = exe.zip
Type = zip
Physical Size = 297

    
Enter password (will not be echoed): Jude Milhon
Everything is Ok

Size:       124
Compressed: 297
$ cat flag.txt 
CodeCamp18{Tal_vez_las_mujeres_no_seamos_buenas_para_la_lucha_física,_pero_sin_duda_sobresalimos_en_el_manejo_del_teclado}
```

Ahí está el flag:
`CodeCamp18{Tal_vez_las_mujeres_no_seamos_buenas_para_la_lucha_física,_pero_sin_duda_sobresalimos_en_el_manejo_del_teclado}`
