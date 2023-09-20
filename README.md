# steganography-for-everyone

 How-to zine for a workshop on DIY steganography

Steganography workshop

Project 1:
Cat trick to put a pdf on an image
-> separate in a hex editor

Project 2:
OpenStego
https://www.openstego.com
-> install Java first

Hide a text file in a photo

Tip: Use a new image

Project 3:

Steghide via Steganography Toolkit
https://github.com/DominicBreuker/stego-toolkit

Start Docker.

`docker pull dominicbreuker/stego-toolkit`

## Launch interactive shell

```
cd ~/Desktop
mkdir data
docker run -it --rm -v $(pwd)/data:/data steghide-docker /bin/sh
```

## Embed data non-interactively

```
docker run --rm -v $(pwd)/data:/data steghide-docker steghide embed -f -ef /data/secret.txt -cf /data/photo.jpg -p iffybooks -sf /data/stego_file.jpg
```

## Extract data non-interactively

```
docker run -it --rm -v $(pwd)/data:/data steghide-docker steghide extract -sf /data/stego_file.jpg
```

## Further reading ...

dominicbreuker/stego-toolkit
