# Steps for setting up Windows + WSL under new profile
Before starting, check for Windows updates and install windows package manager
Launch Powershell w/ admin rights and follow steps:

```
winget install -e --id Microsoft.VisualStudioCode
winget install -e --id SublimeHQ.SublimeText.4
winget install -e --id Microsoft.Teams
winget install -e --id Git.Git
winget install -e --id 7zip.7zip
winget install -e --id GitHub.cli
wsl --install
```

## Azure
```
winget install -e --id Microsoft.AzureStorageExplorer
winget install -e --id Microsoft.AzureCLI
```

## GCP
```
winget install -e --id Google.CloudSDK
```

## Install and configure pyenv, windows fork - make sure to use a version relevant for your project
```
Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
[System.Environment]::SetEnvironmentVariable('PYENV',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")
[System.Environment]::SetEnvironmentVariable('PYENV_ROOT',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")
[System.Environment]::SetEnvironmentVariable('PYENV_HOME',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")
[System.Environment]::SetEnvironmentVariable('path', $env:USERPROFILE + "\.pyenv\pyenv-win\bin;" + $env:USERPROFILE + "\.pyenv\pyenv-win\shims;" + [System.Environment]::GetEnvironmentVariable('path', "User"),"User")
pyenv install 3.8.10
pyenv global 3.8.10
```


## Git config - make sure to update with your details
```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git config --global credential.https://dev.azure.com.useHttpPath true
```

## VSCode extensions
```
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension eamodio.gitlens
code --install-extension editorconfig.editorconfig
code --install-extension ms-vscode.powershell
code --install-extension hashicorp.terraform
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension innoverio.vscode-dbt-power-user
```



## WSL - run using WSL terminal, and make sure to update with your details
```
sudo apt-get install jq
sudo apt-get -y update
sudo apt-get install zsh
sudo apt-get install git
sudo apt-get install gcc
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git config --global credential.helper "/mnt/c/Program\\ Files/Git/mingw64/libexec/git-core/git-credential-wincred.exe"
curl https://pyenv.run | bash
echo 'export PATH="$HOME/.pyenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
source ~/.zshrc
pyenv install 3.8.13
pyenv global 3.8.13
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install terraform
sudo apt-get install apt-transport-https ca-certificates gnupg 
```

### GCP
```
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
sudo apt-get update && sudo apt-get install google-cloud-cli
gcloud init --no-launch-browser
```
