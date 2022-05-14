# SCUT华南理工大学2022无限机甲杯，stm32双芯控制底盘程序开源

#### 介绍
    为了尽可能精确控制机器，因此我们打算拨盘电机、两个发射电机均使用带编码器的电机以获取转速，但由此就会导致stm32开发板的定时器资源不够用
    因此选择了双芯控制方案，以板1作为PS2接收器，并且用于控制云台等发射机构电子零件，板2从板1接收运动模式的信号，进行底盘控制

#### 软件架构
使用stm32CubeMX生产项目文件，然后使用keil编写程序、编译以及下载程序，编程语言为c语言

#### 使用说明
    1. 因发射机构程序并未写完，故只上传的底盘控制程序，应该用于控制发射机构的板1的已配置针脚与代码较少
    2. 若用cubeMX生产板1的工程文件后，之前设置的c语言include path的内容将移动到misc control中，会造成编译错误，因此在重新生产板1的工程文件后，因右键main.c，选择菜单第一项，再选择弹出的窗口上方的"C/C++"，将misc control中的内容复制到include path中
    3. PS2手柄使用SPI外设进行接收数据，按键与程序变量的关系请看以下代码
                 printf(" Lx: %d Ly: %d Rx: %d Ry: %d    ",XY[2],XY[3],XY[0],XY[1]);
                 for(i1 = 0;i1 < 16;i1++)
                    {
                	if(All_But[i1]) 
                	{
                		switch(i1)
                		{
                			case(0): printf(" Left");break;
                			case(1): printf(" Down");break;
                			case(2): printf(" Right");break;
                			case(3): printf(" Up");break;
                			case(4): printf(" Start");break;
                			case(5): printf(" Select");break;
                			case(6): printf(" Left");break;
                			case(7): printf(" Select");break;
                			case(8): printf(" Square");break;
                			case(9): printf(" Cross");break;
                			case(10): printf(" Circle");break;
                			case(11): printf(" Triangle");break;
                			case(12): printf(" R1");break;
                			case(13): printf(" L1");break;
                			case(14): printf(" R2");break;
                			case(15): printf(" L2");break;			
                		}
                	}
                    }
                    printf("被按下\n");	
        
