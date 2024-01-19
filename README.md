# Nokia实习项目——Test Skill Assessment System

## 1. 业务介绍

​	用户上传题目，系统分配专家审核，根据审核结果触发后续相应事件

### 1.1 业务要求

- 用户可以上传选择题/问答题
- 用户可以上传图片，指定题目有效期
- 用户可以在未完全确认时先存草稿，同理上传题目时要检查题目的完整性
- 用户可以随时取消上传
- 审核人可以发起Comment并在有未关闭的Comment时不允许通过题目
- 审核人可以在题目审核未结束时撤销之前的决定
- 用户与审核人应在适当事件收到邮件提醒
- 最长审核时间应有限制，过期自动视为审核失败
- 审核所需人数，审核有效期，题目可选有效期等应作为系统参数供管理员设定
- 用户和审核人可以筛选不同状态的题目查看
- 用户可以管理自己所有审核完成的题目

### 1.2 业务流程设计图

四个泳道分别对应用户，审核人，question_review数据库表，question数据库表的行为与事件

![][UserUploadQuestion]

### 1.3 新增类关系图

新增四个数据库表：

- question_review 记录题目审核事件
- question_review_timer 处理审核超时事件
- comment 审核人与用户聊天记录
- question_timer 处理题目有效期

![][UserQuestion]

### 1.4 新增HTML邮件

​	这里忘记截图了，使用HTML格式邮件通知上传人/审核人相应事件

- 通知审核人分配到了审核任务

- 通知上传人题目已被通过

- 通知上传人审核已经超时，自动被拒绝

- 通知上传人题目被拒绝

- 通知审核人即将到期

  

## 2. 实现效果展示

### 2.1 首页

​	右上角可快速添加题目

![][home]

### 2.2 侧栏工具页

​	Upload Question 和Reviewing Management为新添加的页面菜单

![][homeMargin]

### 2.3 添加问题页面

​	

![][addQuestion]

### 2.4 添加问题弹窗

​	用户可以选择题目类型（选择题，问答题），指定题目有效期，上传图片，并在未想好时还可以存草稿

​	下图展示了选择题表单样式

![][addQuestionDialog]

### 2.5 专家审核页面

​	专家可以在此查看分配给自己的题目并快速投票/在题目完结前撤销投票

![][rewiwingList]

### 2.6 我的题目页面

​	在此展示用户所有以及审核完的题目，用户可以查看题目历史或删除题目

![][myQuestions]

### 2.7 审核中题目页面

​	在此页面专家与上传人可以相互留言，查看题目编辑，审核历史，预览题目，为题目投票

下图展示了有一位审核人已批准题目，题目仍在审核中

![][rewiewingQuestionStatus]

### 2.8 审核未通过题目

​	题目被一定数量审核人拒绝后会终止题目审核事件并邮件通知题目所有者。下图展示是专家拒绝题目，也可由用户自己取消/题目审核到期

![][rejectedQuestion]

### 2.9 预览题目弹窗

​	专家预览题目时显示题目的详细信息，包括题目领域，难度，题解等等

![][questionPrewiew]

### 2.10 专家投票页面

​	专家在题目还未被通过且没有仍在活跃中的Comment时可以通过题目

![][forbiddenApprove]



[UserUploadQuestion]:./design/UserUploadQuestion.png
[UserQuestion]:./design/UserQuestion.png



[home]:./img/home.png
[homeMargin]:./img/homeMargin.png
[addQuestion]:./img/addQuestion.jpg
[addQuestionDialog]:./img/addQuestionDialog.jpg
[rewiwingList]:./img/rewiwingList.jpg
[myQuestions]:./img/myQuestions.jpg
[rewiewingQuestionStatus]:./img/rewiewingQuestionStatus.jpg
[rejectedQuestion]:./img/rejectedQuestion.jpg
[questionPrewiew]:./img/questionPrewiew.jpg
[forbiddenApprove]:./img/forbiddenApprove.jpg







