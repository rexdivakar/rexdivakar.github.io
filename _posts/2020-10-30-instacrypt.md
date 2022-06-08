---
title: InstaEncrypt
author: rexdivakar
date: 2020-10-30 15:55:00 +0800
categories: [python, InstaEncrypt]
tags: [python, Open-Source, pypi]
math: true
mermaid: true
toc: true # table of contents
comments: true
pin: false
---


## About the Tool

This is an Open Source [AES Standard encrytion](https://www.comparitech.com/blog/information-security/what-is-aes-encryption/) tool,<br />
AES stands for Advanced Encrption Standard. It is a symmetric-key algorithm, meaning the same key is used for both encrypting and decrypting the data.

![AES]({{"/assets/img/aes.jpg"| absolute_url}}){: width="800" height="700" }{: .shadow }
_aes encryption_

AES encryption has three different block ciphers: AES-128 (128 bit), AES-192 (192 bit) and AES-256 (256 bit). These block ciphers are named after the key length they use for encryption and decryption. All these ciphers encrypt and decrypt the data in 128-bit blocks but they use different sizes of cryptographic keys.

![AES DESIGN]({{"/assets/img/aes_design.jpg"| absolute_url}}){: width="600" height="500" }{: .shadow }
_aes design

A file (_temp_key.txt_) for storing the encryption key(s) for file(s)/folder(s) encrypted using the tool is automatically created in the current working directory.<br/>
_Always make sure to backup the encryption key if not the files cannot be reverted back....!!!_

### Built with [Python 3](https://www.python.org/)

### Prerequisites

* Python3<br>
It is preinstalled in Ubuntu 20.04. To check the version use command :

```
python3 --version
```

If it is not preinstalled for some reason, proceed [here][4] and download as per requirement.

* requirements.txt<br>
Run the following command in terminal to download the required packags for running the tool locally :

```
pip install -r requirements.txt
```

## Contributing

1. Fork the Project
1. Create your Feature Branch (git checkout -b feature/aesEncryptionCode)
1. Commit your Changes (git commit -m 'Add something')
1. Push to the Branch (git push origin feature/aesEncryptionCode)
1. Open a Pull Request

_Follow the given commands or use the amazing GitHub GUI_
<br>**Happy Contributing** :)

[contributors-shield]: https://img.shields.io/github/contributors/rexdivakar/Fi1e-EncRypt0R.svg?style=flat-square
[contributors-url]: https://github.com/rexdivakar/Fi1e-EncRypt0R/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/rexdivakar/Fi1e-EncRypt0R.svg?style=flat-square
[forks-url]: https://github.com/rexdivakar/Fi1e-EncRypt0R/network/members
[stars-shield]: https://img.shields.io/github/stars/rexdivakar/Fi1e-EncRypt0R.svg?style=flat-square
[stars-url]: https://github.com/rexdivakar/Fi1e-EncRypt0R/stargazers
[issues-shield]: https://img.shields.io/github/issues/rexdivakar/Fi1e-EncRypt0R.svg?style=flat-square
[issues-url]: https://github.com/rexdivakar/Fi1e-EncRypt0R/issues
[license-shield]: https://img.shields.io/github/license/rexdivakar/Fi1e-EncRypt0R.svg?style=flat-square
[license-url]: https://github.com/rexdivakar/Fi1e-EncRypt0R/blob/master/LICENSE.txt
[0]:https://www.comparitech.com/blog/information-security/what-is-aes-encryption/
[1]:https://www.python.org/
[2]:https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github
[3]:https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository
[4]:https://www.python.org/downloads/
[img1]:https://www.atpinc.com/upload/images/2020/04-22/4e79465eb02f4422a7c4bba9f99ffa09.jpg
[img2]:https://cdn.ttgtmedia.com/rms/onlineImages/security-aes_design_mobile.jpg
[img3]:https://github.com/rexdivakar/Fi1e-EncRypt0R/blob/master/images/Screenshot%20from%202020-10-01%2021-22-14.png
[img4]:https://github.com/rexdivakar/Fi1e-EncRypt0R/blob/master/images/Screenshot%20from%202020-10-01%2021-24-53.png
[img5]:https://github.com/rexdivakar/Fi1e-EncRypt0R/blob/master/images/Screenshot%20from%202020-10-01%2021-26-17.png
[img6]:https://github.com/rexdivakar/Fi1e-EncRypt0R/blob/master/images/Screenshot%20from%202020-10-01%2021-27-23.png
