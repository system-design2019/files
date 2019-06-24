

## 项目结构

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
    ├─privateKey
    │      EmailKey.txt
    │      SMSKey.txt
    │      
    └─static
            mail_forget_password_template.html
            mail_recharge_confirm.html
            mail_register_template.html
            mail_withdraw_confirm.html
```

