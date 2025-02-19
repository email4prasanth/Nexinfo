### Store Bitbucket credentials in server & Clone code 
> NOTE: we are using Method-1
#### Method-1 create a token at profile level (Nexinfo-DataSolutions)multiple repos
##### Steps to Get an App Password:
- Connec the `SSL VPN client software` and launch `Nexinfo -  Linux` you will land at user `ubuntu@nexinfo-dev`.
- Make a directory **nexinforepo**
```sh
mkdir nexinforepo
git clone https://marriprasanthp@bitbucket.org/hubino/data-platform-backend.git
enter the app token here
cd  # Go to home directory
```
- To avoid entering the token every time, you can save credential
```sh
git config --global credential.helper store
```
- For your Ubuntu user (ubuntu), the path is `/home/ubuntu/.git-credentials`
```
cat .git-credentials
```
- Git will remember the token
#### Method-2 Create a token at repo level (data-platform-backend)
##### Steps to Get a Repository Access Token:
- Connec the `SSL VPN client software` and launch `Nexinfo -  Linux` you will land at user `ubuntu@nexinfo-dev`.
- Make a directory **nexinforepo**
```sh
mkdir nexinforepo
git clone https://x-token-auth:YOUR_ACCESS_TOKEN@bitbucket.org/hubino/data-platform-backend.git
cd  # Go to home directory
```
- To avoid entering the token every time, you can save credential
```sh
git config --global credential.helper store
```
- For your Ubuntu user (ubuntu), the path is `/home/ubuntu/.git-credentials`