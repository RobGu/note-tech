# Get Start
## Server
### Installation
- Install MySql
  ```shell
    brew install mysql
    npm install -g code-push-server
    npm install pm2 -g
  ```
### Configuration
- 初始化mysql数据库

  `code-push-server-db init --dbhost localhost --dbuser root --dbpassword `

  - *需要手动到 mysql 创建用户*
  ```sql
  insert into users(username, password, email, identical) values('test', '$2a$12$LwLKZG0UQ/kBCRsB64zJtOdhnN/wow/BRidf4rrjt7s0WImkzqsmi', 'test@.com', 'test');
  ```

- 启动服务

  `code-push-server`
-  浏览器中打开 http://127.0.0.1:3000
  - 用户名 admin
  - 初始密码: 123456
- 更改密码

  `curl -X PATCH -H "Authorization: Bearer ${key}" -H "Accept: application/json" -H "Content-Type:application/json" -d '{"oldPassword":"123456","newPassword":"654321"}' http://192.168.225.138:3000/users/password`

## Client

## 使用 code push 做 hot fix
- 仅适用于没有任何 native 代码改动的情况
- appVersion 和 appStoreVersion 保持不变
- 部署 Staging
  - Android
  ```shell
    code-push release-react test-Android android --deploymentName Staging --targetBinaryVersion x.x.x
  ```
  - iOS
  ```shell
    code-push release-react test-iOS ios --deploymentName Staging --targetBinaryVersion x.x.x
  ```
- 部署 Production
  - Android
  ```shell
    code-push promote test-Android Staging Production --targetBinaryVersion x.x.x
  ```
  - iOS
  ```shell
    code-push promote test-iOS Staging Production --targetBinaryVersion x.x.x
  ```



root@localhost: ,hyM(e_&N9d?
