# 阿里短信接口

[![Latest Stable Version](https://poser.pugx.org/flc/dysms/v/stable)](https://packagist.org/packages/flc/dysms)
[![Total Downloads](https://poser.pugx.org/flc/dysms/downloads)](https://packagist.org/packages/flc/dysms)
![php>=5.4](https://img.shields.io/badge/php->%3D5.4-orange.svg?maxAge=2592000)
[![License](https://poser.pugx.org/flc/dysms/license)](https://packagist.org/packages/flc/dysms)

> PS：**阿里大鱼** [https://github.com/flc1125/alidayu](https://github.com/flc1125/alidayu)

## 安装

```shell
composer require flc/dysms
```

## 使用
<?php
	use Flc\Dysms\Client;
	use Flc\Dysms\Request\SendSms;
	

	$config = [
   	 'accessKeyId'    => 'LTAIbVA2LRQ1tULr',
    	'accessKeySecret' => 'ocS48RUuyBPpQHsfoWokCuz8ZQbGxl',
	];
	
	
	$client  = new Client($config);
	
	$sendSms = new SendSms;
	
	$sendSms->setPhoneNumbers('1500000000');  //手机号
	
	$sendSms->setSignName('叶子坑');          //签名名称（在控制器后台可以看到）
	
	$sendSms->setTemplateCode('SMS_77670013');   //模板code
	
	$sendSms->setTemplateParam(['code' => rand(100000, 999999)]);  这个自动生成的六位数字必须保存起来， 然后作为验证（具体流程，看你的思路）
	$sendSms->setOutId('demo');
	
	print_r($client->execute($sendSms));
	
	//调用成功则会返回一个对象：
   //返回例子： 
   stdClass Object ( [Message] => OK [RequestId] => 595370D6-4B72-4B81-BDFA-3A2CFF31FADE [BizId] => 598713726981087773^0 [Code] => OK )


## 支持

- 官方网址： https://www.aliyun.com/product/sms?spm=5176.8142029.388261.339.WL7atM
- 官方API文档： https://help.aliyun.com/document_detail/55451.html?spm=5176.doc55289.6.556.pMlBIe
- composer： https://getcomposer.org/

## License

MIT
