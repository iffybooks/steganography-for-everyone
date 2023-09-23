<img src="images/a488c4f6d4a90680884d8401ec6c3856652fe2fb.png" title="" alt="Steganography_for_everyone_cover.png" data-align="center">

<div style="page-break-after: always;"></div>

# You should be able to communicate securely when you want to. Steganography is worth knowing about.

If you don't want other people to read your messages, you can use **cryptography** to scramble your message so that no one else can read it. If someone's looking over your shoulder, however, they'll be able to see that you're sending/receiving messages that look scrambled. 

If you don't want your adversary to see your scrambled message and get wise to what you're doing, you can use **steganography** to conceal your secret message in something innocuous, like a photo of a sunset.

Here are some ways you could use steganography:

• Exchange off-the-record messages via ordinary email, hidden in vacation photos.

• Run a photo blog with the location of a secret rave embedded in every image, readable by folks with the password.

• Store something personal (like a private encryption key or your diary) in a photo of your cate.

• Create an elaborate alternate reality game with a series of riddles hidden in photos scattered across the web, taking players on a twisty path that leads to your Bandcamp page.

We're approaching this project with a spirit of old-school hacker curiosity. We like trying things out and seeing what's possible. But we're super ethical, super antifascist, and we don't have time for libertarian nonsense. If you’re trying to do something creepy/right-wing with the knowledge in this zine, please fuck off and leave us alone. We don't want anything to do with you.

Now that the pleasantries are out of the way, let's get started!

## Overview

In this workshop you'll use the command-line program **steghide** to hide secret, encrypted messages inside JPEG image files.

If you're using Linux, you should be able to install steghide with your package manager. Installing steghide on macOS & Windows is trickier, so we recommend running it via Docker. 

You can find this zine on our website at the following URL:
https://iffybooks.net/steganography-for-everyone

Source code and example files are on GitHub:
https://github.com/iffybooks/steganography-for-everyone

## Take a photo

You'll start by creating two files: a JPEG image and a smaller file you'll conceal inside it.

For the JPEG file, you'll want to use an image that isn't available elsewhere on the web. Here's why:

Let's say you grab a photo from a stock photo site, hide your secret message in it, and post the updated image file on your blog. If an adversary suspects you're using steganography, they can do a reverse image search and find the original file. If the images look similar but the JPEG on your site is slightly larger, that's a clue you may be using steganography.

❏ Take a photo using your phone or a digital camera.

## Transfer the photo to your computer

❏ Go to your desktop and create a new directory called `data`. 

❏ Transfer your new photo to your computer and put it in the `data` directory you just created. 

↳ You can transfer the file using cloud storage, but then you've made a copy of the original file that can hypothetically be compared to the version with a hidden message. Best to avoid cloud storage if possible, at least for this workshop.

↳ If you're using iOS and macOS, transferring the file via AirDrop is a good option.

↳ For both iOS and Android, you can get an adapter that lets you connect a USB thumb drive or microSD card to your phone. It's a handy trick for transferring files to a computer without using the internet.

<img title="" src="images/182a671f9a81134f0b3c2732e8a0cdee8f2d1702.jpg" alt="th-3964907078.jpg" width="226" data-align="center">

## Convert your photo into a JPEG with ImageMagick

If you're using a digital camera or an Android phone, the photo you transferred to your computer is probably already in JPEG format. If so, the filename will end with ".jpg" or ".jpeg".

If you're using an iPhone, you

Install ImageMagick

```
convert example_image.png example_image.jpg
```

```
convert -resize 50% IMG_5042.HEIC IMG_5042.jpg
```

## Transfer the photo to your computer

## Create your secret message

## Choose a good passphrase

It's *very* important to use a strong password. We'd recommend 20 characters or more to be on the safe side.

One way to get through password protection is to use a **brute force** attack, which involves guessing thousands, millions, of billions of possible passwords until one works. Brute force attacks aren't practical for online services like email, because the service provider will shut off access after a certain number of guesses. 

For email, an 8-character password like "Ql?e2HwX" is probably fine. For an encrypted file, there's a reasonable chance someone will be able to 

<img title="To anyone who understands information theory and security and is in an infuriating argument with someone who does not (possibly involving mixed case), I sincerely apologize." src="images/password_strength.png" alt="Password Strength" data-align="center" width="540">

Printable Diceware List:
https://iffybooks.net/Diceware_List.pdf

CaravanYenGraphFailing

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

## 

## 

# Mac + Windows Instructions

## ## Download the project code

https://github.com/iffybooks/steganography-for-everyone

## Download and install Docker

## 

## 

## Build the Docker image

❏ 

```
cd /Users/iffybooks/Downloads/steganography-for-everyone/steghide-docker 
```

❏ 

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

## Remove all image metadata with exiftool

## Hide a longer file in a photo

## Caveats

Social media sites like Instagram and Facebook will re-compress every image you upload, which will most likely destroy your hidden message. Just a heads-up.

It's possible your hidden message will be able to be detected in the future if someone finds a flaw in the way steghide works.

Writing down your password is a liability, so be thoughtful about it.

Be careful who you share passwords with.

Depending on your situation, having steghide installed on your computer may look suspicious. Uninstalling things when you're done is an option.

## Further reading

- Steghide official quick start page:
  https://steghide.sourceforge.net/documentation.php

- Steghide man page (manual):
  https://steghide.sourceforge.net/documentation/manpage.php

- Steganography Toolkit (a Docker image with various steganography tools preinstalled)
  https://github.com/DominicBreuker/stego-toolkit
  
  Run this command to download the image: `docker pull dominicbreuker/stego-toolkit`

<div style="page-break-after: always;"></div>

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />

<img src="images/453eacede0b6ddf49a2ebc7bb7bad9b852f26d35.png" title="" alt="Ditto_pin_v3.png" width="95">

**Anti-copyright 2023**

**iffybooks.net/steganography-for-everyone**

<br />
<br />

**Iffy Books**&nbsp;

**319 N. 11th St. #2I, PHL**
