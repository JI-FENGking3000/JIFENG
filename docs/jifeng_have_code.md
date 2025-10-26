## 小车的设计思路过程
1. 先开始想到采取吸入式（类似于吹风机原理）来收集小球
2. 后面根据小球的实际大小和质量，改变策略，采取滚筒式，并结合舵机运动来收集小球
## 相关知识的学习过程
1. 下载fusion360或solidworks，并开始学习建模相关知识，学习画草图，实体练习，以及装配体练习（tjj，lc）
2. 下载dev++,观看翁恺c语言，学习c语言到指针，了解基本的逻辑(lym,myw,lxf)
3. 下载keil5,cubemx,学习江科大stm32到通信协议和hal库的使用方法
4. 参与3D打印培训学习在建模时需要注意哪些细节，以及导入导出文件该怎么做，并下载OrcaSlicer
5. 进行电控相关的培训
## 小车基础功能展示（详情视频请见文件）
1. 【外形展示】
2. 【马达运动（单一）】
3. 【马达运动（单一）】
4. 【底盘运动（单一）】
5. 【马达运动（全部）】
6. 【底盘运动（全部）】
		if (ps2.btn1==0x20 ){    //车体向右
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_5,GPIO_PIN_SET);//前IN2 
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_4,GPIO_PIN_RESET);//IN1
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_3,GPIO_PIN_RESET); //IN4 
          HAL_GPIO_WritePin(GPIOA,GPIO_PIN_15,GPIO_PIN_SET);//IN3
          HAL_GPIO_WritePin(GPIOA,GPIO_PIN_3,GPIO_PIN_SET);//后IN1
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_4,GPIO_PIN_RESET);//IN2
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_5,GPIO_PIN_RESET);//IN3
          HAL_GPIO_WritePin(GPIOB,GPIO_PIN_6,GPIO_PIN_SET);//IN4
          __HAL_TIM_SetCompare(&htim4,TIM_CHANNEL_1,100);
          __HAL_TIM_SetCompare(&htim4,TIM_CHANNEL_3,100);}

7. 【尺尺寸规范】
8. 【弹丸携带（单一）】
9. 【弹丸携带（全部）】
10. 【结构稳定性】
11. 【舵机运动】
		if(ps2.btn1==0x40){
          __HAL_TIM_SetCompare(&htim1,TIM_CHANNEL_1,500);
          __HAL_TIM_SetCompare(&htim1,TIM_CHANNEL_2,500);
      	}
      	if(ps2.btn1==0x10){
          __HAL_TIM_SetCompare(&htim1,TIM_CHANNEL_1,2500);
          __HAL_TIM_SetCompare(&htim1,TIM_CHANNEL_2,2500);
    	  }
我们的进阶功能作用是通过滚筒升降进行折叠            1.在滚筒折叠时增强小车移动能力，可以快速接近小球。在接近小节后再放下滚筒进行收集，提高收集效率
   2.通过机械臂向后折叠，减小机器人的长度，这样可以使用更大的毛刷，提高收集效率并增加能够收集的球的总数，并且不会超出规则限制
## 	 小车的构建过程
 1  扎带固定比螺丝更方便而且易拆卸
 [![1](1 "1")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/2FCB73F15FBFE074B0749F4FB577D50E.jpg?raw=true "1")
 2 斜板设计配合毛刷的扫球进程,让小球能够进入箱体 [![2](2 "2")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/7DC9ABF211B8A7C07C2B3E95F4EC0981.jpg?raw=true "2")
3 接收器外接便于检查信号的接收情况[![3](3 "3")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/9FE97A3C49FAA9720BB3DD3F395BA80A.jpg?raw=true "3")
4 配合设计的外部支撑让零件更加稳定,可适应抗摔测试[![4](4 "4")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/2FCB73F15FBFE074B0749F4FB577D50E.jpg?raw=true "4")
5 stm32外接便于烧录更改后的代码,加上电源外放能够及时更换电池[![5](5 "5")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/3937203D6BD58F1E61C8A056C96B90A3.jpg?raw=true "5")
6 连轴器设计连接马达和毛刷,且提供外杆支撑用于舵机升降, **关于滚筒升降的设计是为了防止长度超标,且提供外杆支撑用于舵机升降,让其初始状态为滚筒立于箱体之上**[![6](6 "6")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/8449FBAD62242D3A44999877B8F155D9.jpg?raw=true "6") [![7](7 "7")](https://github.com/JI-FENGking3000/JIFENG/blob/main/images/7DC9ABF211B8A7C07C2B3E95F4EC0981.jpg?raw=true "7")