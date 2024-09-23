# SSH Brute-Force Cracking Tool

## 简介

这是一个用于SSH暴力破解的工具，支持多种模式，包括用户名和密码字典攻击、RSA密钥攻击、文件传输和密码猜测等功能。

## 功能

- **client**: 使用用户名和密码字典进行SSH连接尝试。
- **rsa**: 使用RSA密钥和密码字典进行SSH连接尝试。
- **trans**: 文件传输功能，包括上传和下载文件。
- **login**: 使用指定的用户名和密码进行SSH登录。
- **rsa-login**: 使用指定的RSA密钥和密码进行SSH登录。
- **guess**: 使用猜测的密码进行SSH连接尝试。

## 安装

1. 克隆此仓库到本地：
    ```bash
    git clone https://github.com/yourusername/ssh-brute-force-tool.git
    cd ssh-brute-force-tool
    ```

2. 安装所需的Python库：
    ```bash
    pip install -r requirements.txt
    ```

## 使用方法

### 命令行参数

- `--mode`: 模式选择，可选`client`、`rsa`、`trans`、`login`、`rsa-login`、`guess`。
- `--stmpPath`: 邮箱配置文件路径。
- `--hostname`: 目标主机IP地址。
- `--port`: 目标主机SSH端口，默认为22。
- `--username`: 目标主机用户名（模式`login`、`rsa-login`需要）。
- `--password`: 目标主机密码（模式`login`需要）。
- `--rsa_password`: 目标主机RSA私钥密码（模式`login`、`rsa-login`需要）。
- `--guessNum`: 猜测次数，默认为10次（模式`guess`需要）。
- `--attemptRate`: 每秒尝试密码次数。

### 示例

1. 使用用户名和密码字典进行SSH连接尝试：
    ```bash
    python sshcrack.py --mode client --hostname 192.168.1.1 --attemptRate 5
    ```

2. 使用RSA密钥和密码字典进行SSH连接尝试：
    ```bash
    python sshcrack.py --mode rsa --hostname 192.168.1.1 --attemptRate 5
    ```

3. 文件传输功能：
    ```bash
    python sshcrack.py --mode trans --hostname 192.168.1.1 --attemptRate 5
    ```

4. 使用指定的用户名和密码进行SSH登录：
    ```bash
    python sshcrack.py --mode login --hostname 192.168.1.1 --username root --password admin123456 --attemptRate 5
    ```

5. 使用指定的RSA密钥和密码进行SSH登录：
    ```bash
    python sshcrack.py --mode rsa-login --hostname 192.168.1.1 --username root --rsa_password my_rsa_password --attemptRate 5
    ```

6. 使用猜测的密码进行SSH连接尝试：
    ```bash
    python sshcrack.py --mode guess --hostname 192.168.1.1 --username root --password admin123456 --guessNum 10 --attemptRate 5
    ```

### 配置文件

配置文件`data.conf`用于存储邮箱相关的配置信息，格式如下：

- `sender`: 发送人的QQ邮箱，例如`xxxxxx@qq.com`。
- `pw`: 在[QQ邮箱设置页面]可以查看，注意填写的是授权码，不是QQ邮箱密码。
- `receivers`: 接收人的QQ邮箱，例如`xxxxxxxx@qq.com`。

## 注意事项

- 确保配置文件的权限设置正确，防止未经授权的访问。
- 使用工具时请遵守相关法律法规，不要用于非法用途。

## 许可证

本项目使用MIT许可证，详情请参阅LICENSE文件。