# Steganography for everyone!

Steghide via 

## Convert an image into a JPEG with ImageMagick

```
convert example_image.png example_image.jpg
```

```
convert -resize 50% Kit_Poster_for_School_Sept_2023.HEIC Kit_Poster_for_School_Sept_2023.jpg
```

# Steghide instructions for Linux

## Install Steghide

```
sudo apt install steghide
```

## Embed data in a JPEG file

```
cd ~/Desktop
mkdir data
cd data
```

```
steghide embed -f -ef secret.txt -cf photo.jpg -sf /data/stego_file.jpg
```

You'll be prompted to enter a passphrase.

## Extract data from a JPEG file

```
steghide extract -sf stego_file.jpg
```

# Mac + Windows Instructions

## Download and install Docker



## Build the Docker image

```
cd /Users/iffybooks/Downloads/steganography-for-everyone/steghide-docker 
```

```
docker build -t steghide-docker .
```

Here's what the Dockerfile looks like:

```
FROM debian
RUN apt-get update \
    && apt-get install -y steghide  \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /data
```

## Prepare your data

```
cd ~/Desktop
mkdir data
```

Go to your desktop and find the directory called **data**. Put a JPEG photo into the directory, along with a smaller file you're planning to hide.

## Embed data in a JPEG file

```
docker run -it --rm -v $(pwd)/data:/data steghide-docker steghide embed -f -ef /data/secret.txt -cf /data/photo.jpg -sf /data/stego_file.jpg
```

## Extract data from a JPEG file

```
docker run -it --rm -v $(pwd)/data:/data steghide-docker steghide extract -sf /data/stego_file.jpg
```

## Launch interactive shell (for troubleshooting)

```
cd ~/Desktop
mkdir data
docker run -it --rm -v $(pwd)/data:/data steghide-docker /bin/sh
```

## Further reading

Steganography Toolkit
https://github.com/DominicBreuker/stego-toolkit

`docker pull dominicbreuker/stego-toolkit`
