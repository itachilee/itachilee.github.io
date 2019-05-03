---
title: python 实现微信自动回复
date: 2019-05-03 17:08:20
tags: python
categories: 
---

​	

```python
!/usr/bin/env python
 -*- coding:utf-8 -*-
import itchat, time, sys,re
from itchat.content import *
import codecs

def output_info(msg):
    print('[INFO] %s' % msg)

def open_QR():
    for get_count in range(10):
        output_info('Getting uuid')
        uuid = itchat.get_QRuuid()
        while uuid is None: uuid = itchat.get_QRuuid();time.sleep(1)
        output_info('Getting QR Code')
        if itchat.get_QR(uuid): break
        elif get_count >= 9:
            output_info('Failed to get QR Code, please restart the program')
            sys.exit()
    output_info('Please scan the QR Code')
    return uuid

uuid = open_QR()
waitForConfirm = False
while 1:
    status = itchat.check_login(uuid)
    if status == '200':
        break
    elif status == '201':
        if waitForConfirm:
            output_info('Please press confirm')
            waitForConfirm = True
    elif status == '408':
        output_info('Reloading QR Code')
        uuid = open_QR()
        waitForConfirm = False
userInfo = itchat.web_init()
itchat.show_mobile_login()
itchat.get_friends(True)
output_info('Login successfully as %s'%uuid)
itchat.start_receiving()


@itchat.msg_register([TEXT])
def text_reply(msg):	
	#re 
	match=re.search(ur"[\u4e00-\u9fa5]",u"年")
	if match:		    
	#if msg['Type'] == 'Text':
		return u'系统记录，你刚才说了\"%s\"?' % msg['Content']
    	
@itchat.msg_register([PICTURE, RECORDING, VIDEO, SHARING])
def other_reply(msg):
    return u'恩，斗图谁怕谁%s' % 'XD'
	# 图片
itchat.run()

```

