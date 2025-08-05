# KaliWSLSetup

> https://raw.githubusercontent.com/microsoft/WSL/master/distributions/DistributionInfo.json

sudo sed -i "s@http://http.kali.org/kali@https://mirrors.tuna.tsinghua.edu.cn/kali@g" /etc/apt/sources.list

## step 1

wget https://http.kali.org/kali/pool/main/k/kali-archive-keyring/kali-archive-keyring_2025.1_all.deb

sudo dpkg -i kali-archive-keyring_2025.1_all.deb

## step 1 (other)
sudo apt -o Acquire::AllowInsecureRepositories=true -o Acquire::AllowDowngradeToInsecureRepositories=true update

sudo apt -o Acquire::AllowInsecureRepositories=true -o Acquire::AllowDowngradeToInsecureRepositories=true install gnupg -y

sudo wget -q -O /etc/apt/trusted.gpg.d/kali-archive-key.asc https://archive.kali.org/archive-key.asc

## step 2

sudo apt update -y

sudo apt upgrade -y

sudo apt install manpages manpages-zh locales apt-transport-https ca-certificates gnupg lsb-release wget curl zsh git make gcc g++ zstd fastfetch -y

echo "LANG=zh_CN.utf8" | sudo tee /etc/default/locale

## step 3 install rootca

> https://github.com/smallstep/cli/releases

sudo dpkg -i step-cli_*.deb

step certificate install *.crt --all

## step 4 install python

> https://github.com/conda-forge/miniforge/releases/

pip config set global.index-url https://xxxx.com/lowinli/devpi/+simple/

pip config set global.trusted-host xxxx.com

#pip config debug # find config file

#mkdir ~/.pip

#echo -e "[global]\nindex-url = https://xxxx.com/lowinli/devpi/+simple/\ntrusted-host = xxxx.com" | tee ~/.pip/pip.conf

pip install notebook duckdb jupyterlab-language-pack-zh-cn

pip install pandas sympy pydes pyaes pycryptodomex pillow pyshark dpkt brotlipy certifi cffi chardet cryptography idna pip pycosat pycparser openpyxl urllib3 requests ipywidgets ipykernel pyOpenSSL PySocks gevent

pip install SQLAlchemy pymysql networkx tqdm rich
