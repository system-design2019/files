# 架构问题

## 技术选型

### 跨平台性

//前端来写

### 技术选型理由

//后端来写

## 架构设计

### 前端架构设计

//前端来写

### 后端架构设计

//后端来写

- 技术栈

  **Java 1.8.0 + Spring Boot + MySQL5.5 + MyBatis**

- 开发环境

  **IntelliJ Idea + Java 1.8.0 + Spring Boot + MySQL5.5(服务器上)** 

- 部署环境

  **Java 1.8.0 + MySQL5.5+ Tomcat(9.0)(内嵌)**

#### 工程结构

```
├─java
│  ├─META-INF
│  │      MANIFEST.MF
│  │      
│  └─xyz
│      └─timoney
│          └─swsad
│              │  SwsadApplication.java
│              │  
│              ├─bean
│              │  │  Message.java
│              │  │  MoneyRecord.java
│              │  │  Util.java
│              │  │  
│              │  ├─errands
│              │  │      Errands.java
│              │  │      Errands_temp.java
│              │  │      Participant.java
│              │  │      Participant_temp.java
│              │  │      
│              │  ├─questionnaire
│              │  │      Infos.java
│              │  │      Ques1.java
│              │  │      Ques2.java
│              │  │      Ques2_temp.java
│              │  │      QuesContent.java
│              │  │      QuesResult.java
│              │  │      QuesResult_temp.java
│              │  │      Questionnaire.java
│              │  │      Questionnaire_temp.java
│              │  │      User_temp.java
│              │  │      
│              │  ├─quesUser
│              │  │      QuesCollectUser.java
│              │  │      QuesFillUser.java
│              │  │      
│              │  └─user
│              │          Code.java
│              │          Converter.java
│              │          Notification.java
│              │          User.java
│              │          UserState.java
│              │          
│              ├─config
│              │      WebConfig.java
│              │      
│              ├─controller
│              │      Controller.java
│              │      ErrandsController.java
│              │      MoneyController.java
│              │      NotificationController.java
│              │      QuestionnaireController.java
│              │      UserController.java
│              │      VerifyCodeController.java
│              │      
│              ├─Exception
│              │      GlobalExceptionHandler.java
│              │      MyException.java
│              │      
│              ├─intercepter
│              │      CookieIntercepter.java
│              │      
│              ├─mapper
│              │      ErrandsMapper.java
│              │      MoneyMapper.java
│              │      NotificationMapper.java
│              │      QuesCollectUserMapper.java
│              │      QuesFillUserMapper.java
│              │      QuestionnaireMapper.java
│              │      UserMapper.java
│              │      
│              ├─service
│              │      Email.java
│              │      JwtHelper.java
│              │      SMS.java
│              │      
│              └─singleton
│                      SingletonMybatis.java
│                      
└─resources
    │  application.properties
    │  spring-mybatis.xml
    │  
    ├─mappers
    │      errandsMapper.xml
    │      moneyMapper.xml
    │      notificationMapper.xml
    │      quesCollectUserMapper.xml
    │      quesFillUserMapper.xml
    │      questionnaireMapper.xml
    │      userMapper.xml
    │      
    ├─privateKey	//阿里云短信推送和邮件推送的私钥，不放在git里
    │      EmailKey.txt
    │      SMSKey.txt
    │      
    └─static	//邮件推送的模板
            mail_forget_password_template.html
            mail_recharge_confirm.html
            mail_register_template.html
            mail_withdraw_confirm.html
```



### 逻辑视图

### 物理视图

![](./pic/Physical-view.png)

### 开发视图

![](./pic/Development-View.png)

### 处理视图

//后端画一下，不用太正规

## 模块划分

//后端写一下

## 重难点

