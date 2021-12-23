## 21.11 迭代总结

#### 这个迭代个人工作质量较差，Bug数量较多，故专门总结一下个人这个迭代的问题。

#### [Bug List](http://qc.feifanuniv.com/issues/?filter=14689)
#### [Task List](http://qc.feifanuniv.com/issues/?filter=14717)

### 对每个Bug进行单独分析

## 代码自测不充分导致

* #### [返回按钮跳转页面400](http://qc.feifanuniv.com/browse/QSC-34143)
##### 原因：修改了Module的Url层次，但是对于已存在的代码没有筛查进行Url的替换
* #### [复制代码后没有修改对应业务的提示语](http://qc.feifanuniv.com/browse/QSC-34497)
##### 原因：复制代码后没有进行检查Tip这些细节的地方
* #### [多选框未取消选定](http://qc.feifanuniv.com/browse/QSC-34500)
##### 原因：多选框在页面未被刷新的时候，进行了全选，然后关闭弹窗再次打开后没有先处理选中状态。 （踩坑：使用$("input[type='checkbox']").attr('checked', true)时， 如果一个方法连续设置两次attr, 第二次不生效。 应该使用prop方法来设置）
* #### [导出文件错位](http://qc.feifanuniv.com/browse/QSC-34513). [导出文件错位2](http://qc.feifanuniv.com/browse/QSC-34704)
##### 原因：开发完成后需求有变更，导致这边漏改
* #### [导入错误详情页无法打开](http://qc.feifanuniv.com/browse/QSC-34515)
##### 原因：sql书写错误，误把导入的异步任务类型写成了导出的类型
* #### [面包屑主页跳转400](http://qc.feifanuniv.com/browse/QSC-34596). [面包屑主页跳转400(2)](http://qc.feifanuniv.com/browse/QSC-34700)
##### 原因：同第一个Bug 修改了Module的Url层次，但是对于已存在的代码没有筛查进行Url的替换
* #### [高职多出函授站筛选框](http://qc.feifanuniv.com/browse/QSC-34620)
##### 原因：进行高职业务开发的时候，复制过去的代码未检查细节
* #### [面包屑展示错误](http://qc.feifanuniv.com/browse/QSC-34623)
##### 原因：菜单层级改变后，筛查页面面包屑时漏掉
* #### [函授站错误审核学生](http://qc.feifanuniv.com/browse/QSC-34640)
##### 原因：校验审核时，漏掉了函授站老师权限的校验
* #### [未更新Score字段](http://qc.feifanuniv.com/browse/QSC-34649)
##### 原因：数据库表新增了字段，对batchCreate方法进行了修改，漏掉了ON DUPLICATE KEY UPDATE 后面score字段的赋值
* #### [导入弹窗空白](http://qc.feifanuniv.com/browse/QSC-34646)
##### 原因：文件位置变更没有及时修改Controller里面的ModelAndView的返回view path
* #### [导出未添加勾选的列](http://qc.feifanuniv.com/browse/QSC-34663)
##### 原因：开发的时候文档未看到相关需求就没有做，后来看了一下系统中现有的都是会有这个功能就加上了。
* #### [导出未弹toast](http://qc.feifanuniv.com/browse/QSC-34664)
##### 原因：导出按钮的id没有赋值exportBtn，导致asyncTask添加成功后没有找到对应元素
* #### [下载证明材料401](http://qc.feifanuniv.com/browse/QSC-34666)
##### 原因：这里业务逻辑不太熟悉，以为直接把对应的url返回即可。但是这边是七牛的url，需要通过QiniuDownloadHelper获取一下真正的url。
* #### [修改引入](http://qc.feifanuniv.com/browse/QSC-34679)
##### 原因：修改历史遗留Bug时，误动了代码导致
* #### [列缺少函授站](http://qc.feifanuniv.com/browse/QSC-34691)
##### 原因：粗心漏掉
* #### [常量定义位置错误](http://qc.feifanuniv.com/browse/QSC-34693)
##### 原因：js常量定义位置错误
* #### [筛选项不生效](http://qc.feifanuniv.com/browse/QSC-34696)
##### 原因：论文状态的筛选，内部有判断论文是否关闭，修改方法参数为List的时候，未把前端传过来的数值add到List中

* #### [Js ！对于0 返回false](http://qc.feifanuniv.com/browse/QSC-34721)
##### 原因：js 的 ! 运算符 对于 0数值返回了false， 应该判断是否为null

* #### [逻辑运算少了return](http://qc.feifanuniv.com/browse/QSC-34711) http://qc.feifanuniv.com/browse/QSC-34735
##### 原因：判断if的时候未加return

* #### [if else错误](http://qc.feifanuniv.com/browse/QSC-34735)
##### 原因：代码错误导致if else 进入了错误的分支

* #### [页面切换出错](http://qc.feifanuniv.com/browse/QSC-34729) [页面切换出错 2](http://qc.feifanuniv.com/browse/QSC-34731)
##### 原因：1.切换左侧学生列表时，页面未刷新， 再渲染的时候未对被hide的div 进行show操作。 2.重复注册onclick事件


* #### [判断错误](http://qc.feifanuniv.com/browse/QSC-34751)
##### 原因：对于函授站老师的权限判断错误

* #### [状态未赋值默认值](http://qc.feifanuniv.com/browse/QSC-34765)  [状态未赋值默认值（2）](http://qc.feifanuniv.com/browse/QSC-34865)
##### 原因：对于字段status 没有赋值默认值0（未审核）

* #### [模板文件和预填模板文件 不一致](http://qc.feifanuniv.com/browse/QSC-34874)
##### 原因：两类excel文件的字段名未统一导致


* #### [SQL错误](http://qc.feifanuniv.com/browse/QSC-34789)
##### 原因：拿数据时left join了student_degree_application表，导致数据不会为空，应该判断id 是否为0

* #### [Sql书写错误](http://qc.feifanuniv.com/browse/QSC-34776)
##### 原因：Sql写错， 错误的Left join了表，导致被join的表有重复数据，导致返回的数据增加

* #### [校验字段错误](http://qc.feifanuniv.com/browse/QSC-34829)
##### 原因：校验毕业证号的时候取错了字段名

* #### [判断学籍状态错误](http://qc.feifanuniv.com/browse/QSC-34885)
##### 原因：sql中判断学籍状态错误

* #### [Modal 设置display属性导致](http://qc.feifanuniv.com/browse/QSC-34908)
##### 原因：弹出的Modal 错误的设置了display:flex; 导致遮挡了菜单栏

* #### [权限判断错误](http://qc.feifanuniv.com/browse/QSC-34895)
##### 原因：判断学生学位流程开始的时候未添加学校教务老师的判断


## 需求漏做
* #### [校验结果页面漏做](http://qc.feifanuniv.com/browse/QSC-34703)
##### 原因：开发的时候未考虑到这一块

## 修改引入
* #### [函授站老师无法审核学生](http://qc.feifanuniv.com/browse/QSC-34745)
##### 原因：接口返回值遗漏


## 原因总结
* 这次迭代开发时间为9天， 对于迭代任务的时间估算未估算正确，未留出1-2天的测试时间。在迭代发布dev的当天下午才把需求做完，没有足够的时间自测导致一些细节的地方还有一些显而易见的地方进行Fix。
* 这次开发任务涉及旧业务代码变更、旧业务代码高职新增、新业务开发。
* 在开发高职代码的时候未进行 差异排除， 有一些成教有而高职没有的业务点漏掉了。
* 导入导出任务未充分自测，导致bug较多
* 提测dev时质量不好，导致后面时间也一直在修改bug没时间去测试自己做的功能。

## 措施、期望
* 后面迭代加强自己开发质量，对于需求文档多了解、多与PM沟通、多思考提出问题
* 预估开发时间时应仔细考虑任务量，隐藏/关联的任务需要也考虑进去。
* 把握迭代时间，若任务量较多，自己主动多加点班保证进度正常
* 自测时间一定要留出1-2天时间，对照测试用例文件、需求文档进行 覆盖率较高的自测
* 对于细节方面更细心，对照文档字段认真检查


