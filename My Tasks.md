# My Tasks 

## 目录

[TOC]

##近期任务

###机器视觉

- 特征提取算法
  - Haar-like
  - LBP
  - HOG
  - SURF
  - SIFT
  - FAST
  - ORB
- 分类器设计算法
  - SVM
  - ANN
  - 决策树
  - Adaboost
  - 贝叶斯
- matlab，与opencv实现


### easypr学习

###github



###装甲识别

- [x] safeRect()
- [x] 外接矩形的拓展和阈值统计，和相应的辅助函数编写
- [ ] 识别程序HSV尝试，HSV分析工具
- [x] 程序c++类的封装
- [ ] 缩小范围，打分选择
- [ ] 尝试opencv中的svm，与MATLAB对比结果

##发现问题

- [ ] opencv SVM trainAuto
- [ ] 装甲检测，使用blue的检测方法却能检测出红色装甲，使用red的检测方法检测不出蓝色装甲。
- [ ] mexopencv的编译原理，mexopencv.make(), 自己添加相应的函数。
- [ ] MATLAB中要不要将图片数据转换成double

##临时总结

### AutoCAD

- 框选：左右的区别

- 取消选中：ESC

- 双击鼠标中键：调整视图大小；按住鼠标中键：拖动

- 命令栏

- 按钮：捕捉、栅格、正交（F8）

  对象捕捉（右击可以设置捕捉的对象）、对象追踪（标尺的作用）

- 确定键：enter、空格

- ​

### mexopencv与opencv的对比

1. vector -> cell
2. mexopencv中图像中点的坐标还是从(0, 0)开始
3. mexopencv参数传递都是值传递，没有“引用”，“地址”等概念，因此函数必须有返回值，‘’=‘’操作完成变量的拷贝

### Matlab

1. eval(expresion) 将字符串当做表达式运行

2. 字符串分割

   ```matlab
   str = strtrim(str); %去除首位多余空白
   temp_cell = regexp(str, '\s+', 'split'); %使用正则表达式匹配
   ```

3. strrep字符串的替换

4. strcmp字符串比较

5. MATLAB中sum, sort, mean, std，等函数的参数都有一个dim，表示所遍历哪一维数据，例如，当dim=1时，表示遍历第一维数据（即行），求每一列的和。

6. MATLAB函数重载的实现。nargin表示函数参数个数，varargin，表示输入参数的cell数组

7. pause(n) 让程序暂停n秒

8. insertObjectAnnotation(img, shape, position, 'Color', value, ... ) 在图片中做标记

9. MATLAB视频/图片的动态播放

   vision.VideoFileReader对象负责从视频加载图片数据到内存；

   vision.VideoPlayer对象负责将内存中的图片数据交给播放器进行播放。

   ```matlab
   %从视频读取
   reader = vision.VideoFileReader('abc.avi');
   player = vision.VideoPlayer;
   while !isDone(reader)
   	frame = step(reader);
   	step(player, frame);
   end
   release(reader);
   release(player);

   %动态加载图片并进行播放
   list = getFileList('红典型图片');
   videoPlayer = vision.VideoPlayer;
   for i=1:length(list)
       frame = imread(['红典型图片/',list{i}]);
       step(videoPlayer, frame);
   %     pause(50/1000);
   end
   release(videoPlayer);
   ```

   ​

### github

git的**提交**是文件历史状态的`快照` ，Git 中的**分支**，其实本质上仅仅是个指向 commit 对象的可变指针。Git 会使用 master 作为分支的默认名字。在若干次提交后，你其实已经有了一个指向最后一次提交对象的 master 分支，它在每次提交的时候都会自动向前移动。

Git 是如何知道你当前在哪个分支上工作的呢？其实答案也很简单，它保存着一个名为 HEAD 的特别指针。它是一个指向你正在工作中的本地分支的指针（译注：将 HEAD 想象为当前分支的别名）。**每次提交后 HEAD 随着当前分支一起向前移动** 。切换到哪个分支，哪个分支就成为自动向前移动的指针HEAD。

**合并**分两种情况，fast-forward(快进)，分叉合并。前者中两个分支是直系亲属，后者，没有直系关系，但是有共同的祖先。

1. 本地建立库（项目）

   ```shell
   mkdir test
   touch readme.md
   git init #初始化
   git status #查看git状态，随时都可以敲

   ```

2. 添加并提交文件

   ```shell
   git add <filename>
   git commit -m "my first commit"
   ```

3. 新建分支并切换到分支

   ```shell
   git branch <branchname> #新建分支
   git checkout <branchname> #切换分支
   git branch -D <branchname> #删除分支
   ```

4. 打标签

   ```shell
   git tag v1.0 #为当前状态打标签
   git tag #查看所有历史标签
   git checkout v1.0 #切换到v1.0的状态
   ```

5. 与远程仓交互

   ```shell
   #方式1：克隆远程到本地->建立关联->修改提交
   git clone git@github.com:Daibingh/hello.git
   #在修改clone的项目后
   git push origin master
   #方式2：本地有完整项目->与远程仓建立关联->远程本地同步
   git remote add origin git@github.com:Daibingh/test.git
   git push origin master
   ```

6. git常用命令

   **diff**: 比较 两次提交/两个分支/两个文件 的不同

   ```shell
   git diff <id1> <id2> #比较两次提交的不同，提交的id号可以通过 git log 查看
   git diff <branch1> <branch2> #比较两个分支的不同
   git diff <file1> <file2> #比较两个文件的不同
   ```

   **checkout**: 切换分支/tag/提交

   ```shell
   git checkout v1.0 #切换tag
   git checkout xxxxxxxxxxxxxxxxxxxx #切换某次提交之前的状态
   git checkout <branchname> #切换到分支
   ```

   **stash**: 保留当前未完成的工作，用户可以着手去完成别的工作。

   ```shell
   git stash #把当前分支没有commit的代码暂存起来
   git stash list #查看暂存记录
   git stash apply #代码恢复
   git stash drop #删除上一条记录
   ```

   **merge**: 合并分支

   ```shell
   #切换到主分支，然后将分支1合并进来
   git checkout master
   git merge branch1
   #注：rebase 也有合并的功能，与merge有所区别. 合并之后有时会有冲突。
   ```

7. 分支管理

   ```shell
   git branch #查看本地分支
   git branch -r #查看远程分支
   git checkout branchName origin/branchName #将远程分支迁移到本地
   ```

   ​

### MEX

mex文件的编写格式：

```c++
#include "mex.h"
void mexFunction ( int nlhs, mxArray *plhs[], int nrhs, const mxArray *prhs[] )
{
}
```

nlhs 是输出参数个数

plhs 是输出参数指针

nrhs 是输入参数个数

prhs 是输入参数指针

操作输入数据：

mxGetPr 得到数据的指针地址

 mxGetM 和 mxGetN 得到矩阵数据的行和列 (返回整数)

对于实矩阵，我们可以定义 double *M; 来对实矩阵数据操作。

```c++
double *M;
int m,n;
M = mxGetPr(prhs[0]);	//指针指向第一个参数的数据地址
m = mxGetM(prhs[0]);
n = mxGetN(prhs[0]);
```

操作输出数据：

对于输出数据，需要首先用专门的mex函数分配内存空间，

```c++
plhs[0] = mxCreateDoubleMatrix(m,n, mxINT32_CLASS,mxREAL); //生成m x n 的实矩阵
```

同输入数据一样，要对输出数据操作，我们也需要一个指向数据的指针变量，

```c++
double *A;
A = mxGetPr(plhs[0]);
```

注意：MATLAB矩阵数据的存储顺序是"从上到下，从左到右**"**的，这点和Fortran是一样的。也就是说对于MATLAB的m x n的矩阵A。 A(1,1) 就是 *M，A(2,1) 就是 *(M+1) ，以此类推，A(i,j) 就是 *(M + m(j-1) + (i-1))

example:

```c++
#include "mex.h"

void mexFunction ( int nlhs, mxArray *plhs[], int nrhs, const mxArray *prhs[] )
{
   double* pin1, *pin2, *pout;
   int m,n;
   pin1 = mxGetPr(prhs[0]);
   pin2 = mxGetPr(prhs[1]);
   m = mxGetM(prhs[0]);
   n = mxGetN(prhs[0]);
   plhs[0] = mxCreateDoubleMatrix(m,n, mxINT32_CLASS,mxREAL);
   pout = mxGetPr(plhs[0]);
   printf("test mex\n");
   for(int i=0;i<m;i++)
   {
       for(int j=0;j<n;j++)
       {
           *(pout+n*i+j) = *(pin1+n*i+j) + *(pin1+n*i+j);
       }
   }
}
```

在MATLAB中编译：mex test_mex.c

完成后，test_mex就相当于MATLAB中的的函数，可以直接调用。

###c++

获取时间

```c++
//写时间
time_t tm;
time(&tm);
struct tm *t2;
localtime_s(&t2, &tm);
char buf[1024];
strftime(buf, sizeof(buf), "%c", t2);
fs << "calibration_time" << buf;
```

数值类型与string类型的转换

数值类型->string ：

```c++
//利用to_string
int num = 123;
string s = to_string(num);
//利用ostringstream
ostringstream os;
os<<num;
string ss = os.str();
```

string类型->数值类型：

```c++
//利用istringstream
string s = "123";
istringstream is(s);
int num;
is>>num;
```



### opencv

Mat初始化的一种方法：

```c++
//创建一个3*3的矩阵，并初始化
Mat M = (Mat_<double>(3,3) << 1, 0, 0, 0, 1, 0, 0, 0, 1);
```

Mat部分区域选择：

```c++
//单行（列）选择
Mat Mat::row(int i) const;
Mat Mat::col(int j) const;
//多行（列）选择
Mat A,B,C;
B = A(Range(1,3), Range(2,6));
C = A(Range::all(), Range(1,3));
```

Mat的setTo方法：

```c++
//Mat部分或全部赋值
Mat::setTo(InputArray value, InputArray mask = noArray())
```



Mat随机数填充：

```c++
RNG rng(100);
Mat a;
rng.fill(a, RNG::TYPE, InputArray a, InputArray b);
```

type有：UNIFORM, NORMAL

## 备忘录

- [ ] 实现MATLAB解析xml文件，目前只完成dt=d类型的解析，还有其它类型
- [ ] github测试，分支原理，创建，切换，撤销, git flow，git log如何看，head等词语的含义
- [ ] gists

##每天计划

2017.12.21

- [ ] pcs7
- [ ] 复习运控
- [ ] 复习过控
- [ ] 复习先进控制
- [ ] 程序分类整理，上传

2017.12.20

- [x] 还书，续借
- [x] 课程设计
- [x] 过控复习总结
- [ ] 运控复习
- [ ] 先进控制复习

2017.12.13

- [x] 看看别人的装甲检测程序是否出现问题
- [x] 找出问题的根源，统计数据
- [x] 完善相关的函数
- [x] mex与MATLAB
- [ ] opencv cmake pros文件

2017.12.11

- [x] 看easypr的一篇博客
- [x] 完善装甲识别程序，基于统计的思想

2017.12.7

- [x] 装甲检测，MATLAB，和opencv实现，学习熟练图像处理和分析，必要时利用ps做辅助分析
- [x] 比较opencv与MATLAB的相机标定的结果

2017.12.6

- [x] MATLAB相机标定
- [x] 关于比赛本身

2017.12.5

- [x] 角度求解程序分析，测试
- [x] MATLAB相应的相机标定与三维重建
- [x] 根据车牌识别学习图像处理
- [ ] 运控

2017.12.2

- [x] 学习别人的成果
- [x] 看看程序中的角度求解的过程
- [ ] 补充理论知识，看书opencv基础，学习opencv中英文
- [x] Matlab中相机标定与三维重建相关



2017.11.29

- [x] 角度和距离的解决
- [x] 相机标定
- [ ] 车牌识别学习，图像处理

2017.11.28

- [x] 继续研究程序的细节，勘误
- [x] 看程序的效果
- [x] 旋转矩形的角度问题
- [ ] 遍历Mat元素效率比较
- [ ] 红与蓝的区分

2017.11.27

- [x] KNN算法
- [x] Kmeans

2017.11.18

- [ ] Robo视觉程序分析，调试，总结并用新程序编写
- [ ] 字体识别
- [ ] OpenCV stop sign检测

2017.11.17

- [x] 了解比赛所要做的工作，参考往年资料
- [x] OpenCV或MATLAB检测算法
- [x] 打印资料：先进控制、运动控制

2017.11.16

- [ ] matlab级联分类器训练过程、原理，检测车牌
- [ ] OpenCV级联检测器级联分类器，应用
- [ ] Robo视觉程序分析

2017.11.15

- [ ] haar特征与Adaboost分类原理
- [ ] 电机拖动双闭环仿真
- [ ] 电机拖动校正实例仿真，与sisotool对比

2017.11.14

- [x] 总结OpenCV PCA程序收获
- [x] 完善OpenCV程序：路径，数据，num，比对与MATLAB结果
- [x] 看看一副图像保存到XML文件中占多少空间
- [x] OpenCV人脸检测例程分析总结。
- [x] MATLAB PCA程序优化，output file函数
- [ ] MATLAB与OpenCV如何传递数据，之间的接口
- [x] 了解haar特征


