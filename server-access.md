## VPN Installation and connection:
<!-- - [Forticlient Installaion & Connection](https://github.com/email4prasanth/Access_Service/blob/master/VPN/Forticlient.MD)
- [MySQL Installation & Connection](https://github.com/email4prasanth/Access_Service/blob/master/Database/mysql.md)
### Forticlient Installaion: -->
1. Install the latest SSL VPN so􏰂ware on the user's computer.
    - [FortiClient VPN Video](https://www.youtube.com/watch?v=2y5eiaG32cA)
    - [Download and install](https://www.fortinet.com/support/product-downloads)
        - destination folder `C:\Program Files\Fortinet\FortiClient\`
        - Check the connectvity ping 8.8.8.8 in the terminal/command prompt.
        - Disable IPv6 Network and Sharing Center → Change adapter settings, Right-click your active network adapter 
            → Click Properties, Uncheck Internet Protocol Version 6 (TCP/IPv6), **OK**.
        - Restart the system if required.
2. Launch the SSL VPN Client so􏰂ware.
### Forticlient Connection:
3. Open the For􏰀Client Console and go to Remote Access.
4. Add a new connection.
* Set VPN Type to SSL VPN.S
5. Set Username, Description & Remote Gateway to IP address : 103.235.68.52
6. Select Customize Port and enable the check box, set it to 10443.
7. Save your settings.
8. Use the VPN username and Password as below.
Nex***
1L**490
- Sever connection will be displayed.

### Install MySQL on your Ubuntu 24.04.1 LTS server using PowerShell
#### Prerequisites
- PowerShell Remoting: Ensure that PowerShell Remoting is enabled on your Windows machine.
- SSH Access: Ensure that SSH is enabled on your Ubuntu server and you have the necessary credentials (username and password or SSH key).
- Step 1: Establish SSH Connection from PowerShell, `ssh ubuntu@10.1.15.53`, enter your password `Mnb**@**49`.
- Update System's package list and upgrade the existing packages.
```
sudo apt update
sudo apt upgrade -y
```
- check the existing allowed Ports
```
sudo apt install net-tools
sudo netstat -plnt (only tcp)
sudo netstat -tuln (tcp and udp)
```
- Step 3: Install MySQL Server,Check **mysql** database is available.
```
mysql --version
sudo apt install mysql-server -y (or sudo apt install mysql-client-core-8.0)
mysql --version
```
- Step 4: If required Secure MySQL Installation `sudo mysql_secure_installation`.
- Step 5: Configure MySQL to Listen on VPN IP
```
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
bind-address = 10.1.15.53
sudo systemctl restart mysql
sudo systemctl status mysql
```
- Step 6: If rrquired Create a MySQL User for Remote Access
- login, Create a New User and exit
```sh
sudo mysql -u root -p (press enter as password is not set)

SELECT user, host FROM mysql.user; # If nexinfo is restricted to a specific host (like localhost or 10.1.15.53)
DROP USER 'nexinfo'@'10.1.15.53';
CREATE USER 'nexinfo'@'%' IDENTIFIED BY 'Ne***@0**1!';
GRANT ALL PRIVILEGES ON *.* TO 'nexinfo'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;

exit
```
- Step 7: Test the Connection `mysql -h 10.1.15.53 -u nexinfo -p`
- Step 8: Firewall Configuration `sudo netstat -tuln | grep 3306` should see **10.1.15.53:3306** else
```
sudo ufw allow 3306/tcp
sudo ufw reload
sudo netstat -tuln | grep 3306
```
### Mysql testing
- Acess the database `mysql -h 10.1.15.53 -u nexinfo -p`, Now it will launch to **>mysql**
- Check Existing Databases `SHOW DATABASES;`
- Create a New Database 
```
CREATE DATABASE testdb;
SHOW DATABASES;
```
- Use the Database `USE testdb;`.
- Create a Table
```
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
- Show Tables in the Database `SHOW TABLES;`
-  Insert Sample Data
```sh
INSERT INTO users (name, email) VALUES 
('John Doe', 'john@example.com'),
('Jane Doe', 'jane@example.com');
```
- Retrieve Data from the Table `SELECT * FROM users;`.  
- Delete the Database `DROP DATABASE testdb;`.


### Extra:
    - Graphical User Interface (GUI) Method to checkt version
        - Open Firefox.
        - Click the menu button (three horizontal lines ☰) in the top-right corner.
        - Go to Help → About Firefox.
        - A window will pop up showing the Firefox version.
    - check Fireware in my windows system Using Command Prompt (CMD)
        - Open Command Prompt ->   `wmic bios get smbiosbiosversion`  - version is 1.31.0
    - TLS version is TLS 1.2 does the above bios meet the requirement
        - Open Run (Win + R), type inetcpl.cpl, and press Enter.
        - Advanced tab -> Security settings. -> Use `TLS 1.2` or `TLS 1.3`, that’s even better.


ALTER USER 'nexinfo'@'%' IDENTIFIED WITH mysql_native_password BY 'Nexinfo@00291!';
FLUSH PRIVILEGES;


