package sagit;

import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import javax.imageio.ImageIO;

import java.util.Arrays;
import java.util.Random;
import java.lang.Math;
import java.util.Scanner;

public class Sagit {
	
	public static char atc(int ascii) {
		char ch =(char)ascii;
		return ch;
	}
	
	/** 此处设置灰度字符，此处只用十个字符，可以设置更多 */
	private static char[] cs = new char[] {
			'.', ',', '*', '+', '=', '&', '$', '@', '#', ' '
	};
	public static void main(String[] args) throws IOException {
		Scanner number = new Scanner(System.in);
		/*
		 * 107页3.(100道门)
		 */
		boolean[] door = new boolean[100];
		Arrays.fill(door, false);
		for(int i=0;i<100;i++) {
			int doorn = i + 1; //+
			for(int w=1;w<=100;w++) { //门牌号是服务员编号的整数倍则取反
				if(doorn % w == 0) {
					door[i] = !door[i];
				}
			}
			if(door[i]) {
				System.out.println("第" + doorn + "扇门为开");
			}else {
				System.out.println("\t第" + doorn + "扇门为关");
			}
			//System.out.println(door[i]);
		}
		System.out.println("\n" + "\n");

		/*
		 * 107 4
		 * 
		 */
		String[] B = new String[5];
		B[0] = "陈洋";
		B[1] = "马嘉锦";
		B[2] = "洪楚平";
		int[][] BC = new int[3][];
		for(int i=0;i<3;i++) {
			BC[i] = new int[4];
		}
		BC[0][0] = 60;
		BC[0][1] = 61;
		BC[0][2] = 62;
		BC[0][3] = 63;

		BC[1][0] = 91;
		BC[1][1] = 62;
		BC[1][2] = 73;
		BC[1][3] = 84;

		BC[2][0] = 77;
		BC[2][1] = 66;
		BC[2][2] = 55;
		BC[2][3] = 44;
		for(int i=0,i1=1;i<3;i++,i1++) {
			System.out.println(i1 + B[i]);
			
		}
		int p;
		System.out.println("输入学号查看学生成绩：");
		do {
			p = number.nextInt();
			if(p<1 || p>3) {
				System.out.println("输入错误，范围1-3，重新输入：");
				p = -1;
				continue;
			}
			System.out.println(B[p-1] + "的成绩如下：");
			for(int i=0;i<4;i++) {
				switch(i) {
				case 1:
					System.out.println("C语言程序设计:" + BC[p-1][i]);
					break;
				case 2:
					System.out.println("物理：" + BC[p-1][i]);
					break;
				case 3:
					System.out.println("英语:" + BC[p-1][i]);
					break;
				case 4:
					System.out.println("高等数学:" + BC[p-1][i]);
					break;
				}
			}
			
		}while(p==-1);
		System.out.println("\n" + "\n");
		
		/*
		 * 
		 */
		
		/*
		 * 84页三.(1)
		 * 1-80中5的倍数之和
		 * 
		 */
		int a=1;
		int acount = 0;
		while(a<=80){
			if(a % 5 ==0) {
				//System.out.print("5的倍数有：\t");
				//System.out.println(a);
				acount = acount + a;
			}else {
				//System.out.print("不是5的倍数有：\t");
				//System.out.println(a);
			}
			a++;
		}
		System.out.println("5的倍数之和：");
		System.out.println(acount + "\n" + "\n" + "\n");
		
		/*
		 * 84页三.(2)
		 * 输入一批数，计算其中最大 最小值，输入-1结束
		 * 
		 */
		System.out.println("请输入一个整数：（-1结束）");
		int qaq = number.nextInt();;
		int qaqmax = qaq; //最大值
		int qaqmin = qaq; //最小值
		
		if(qaq == -1) {
			System.out.println("你找碴是不是，上来就-1？");
			System.out.println("最大值：" + qaqmax + "\n" + "最小值：" + qaqmin);
		}else {
			do {
				qaq = number.nextInt();
				/*将-1也算上
				if(qaqmax < qaq) {
					qaqmax = qaq;
				}
				if(qaqmin > qaq) {
					qaqmin = qaq;
				}
				//*/
				 //* 如果不将-1算上，则去掉这段注释
				if(qaq == -1) {
					break;
				}else {
					if(qaqmax < qaq) {
						qaqmax = qaq;
					}
					if(qaqmin > qaq) {
						qaqmin = qaq;
					}
				}
				//*/
			}while(qaq != -1);
			System.out.println("最大值：" + qaqmax + "\n" + "最小值：" + qaqmin);
		}
		
		
		/*
		 * 84页三.(3)
		 * 输出矩阵
		 * 
		 */
		int jx = 1;
		int jy = 1;
		int j = 0;
		while(jy <= 4) {
			while(jx <= 5) {
				j = j + jy;
				System.out.print(j + "\t");
				jx++;
			}
			jy++;
			jx = 1;
			j = 0;
			System.out.print("\n");
		}
		

		/*
		 * 数组
		 */
		System.out.print("请输入数组大小：");
		int size = number.nextInt();
		int[] jdprice = new int[size];
		for(int array=0;array<jdprice.length;array++) {
			System.out.print("请输入jdprice[" + array + "]=");
			jdprice[array]=number.nextInt();
		}
		for(int array = 0; array < size; array++) {
			System.out.print(jdprice[array] + " ");
		}		
		/*
		 * 反序输出数组
		 */
		System.out.println("反序输出数组");
		for(int i=jdprice.length-1;i>=0;i--) {
			System.out.print(jdprice[i] + " ");
		}
		System.out.println("\n");
		
		/*
		 * 冒泡排序
		 * 输入后判断大小排序
		 */
		System.out.println("冒泡排序");
		for(int a1=0;a1<jdprice.length-1;a1++) { //a1循环至数组长度
			for(int a2=0;a2<jdprice.length-1-a1;a2++) { //a2循环至数组前一位
				if(jdprice[a2]>jdprice[a2+1]) {
					int ass = jdprice[a2+1];
					jdprice[a2+1]=jdprice[a2];
					jdprice[a2]=ass;
				}
				System.out.print(jdprice[a2] + " ");
			}
			System.out.print("[");
			for(int a2=jdprice.length-1-a1;a2<jdprice.length;a2++) {
				System.out.print(jdprice[a2] + " ");
			}
			System.out.print("]\n");
		}
		double jdavge = 0;
		for(int i=0;i<jdprice.length;i++) {
			jdavge += jdprice[i];
		}
		jdavge = jdavge / jdprice.length;
		System.out.println("平均值=" + jdavge);
		

		System.out.println("\n" + "\n");
		
		
		/*
		 * 鸡兔同笼
		 * 
		 */
		System.out.println("鸡兔一共有多少只：");
		//Scanner t = new Scanner(System.in);
		int t = number.nextInt();
		System.out.println("一共有多少条腿：");
		//Scanner tl = new Scanner(System.in);
		int tl = number.nextInt();
		
		/*
		int t = 12;
		int tl = 28;
		*/
		int ck,rab;
		//Scanner t = new Scanner(System.in);
		ck = (2*t) - (tl/2);
		rab = t - ck;
		//t.close();
		//tl.close();
		if(ck<0 | rab<0) {
			System.out.println("不存在分配方式");
		}else {
			System.out.println("鸡：\t" + ck + "\n" + "兔：\t" + rab + "\n" + "\n");
		}
		

		/*
		 * 狗东网页
		 * 
		 */
		System.out.print("\t" + atc(9619) + atc(9619) + "热爱美好新时代" + atc(9619) + atc(9619)
				+ "\n" + atc(9794) + "手表\t"+ atc(9794) + "高达\t" + atc(9794) + "二手手机\t"+ atc(9794) + "键盘"
				+ "\n" );
		int pp = number.nextInt();
		if(pp == 1) {
			System.out.print("\t" + atc(9619) + atc(9619) + "热爱美好新时代" + atc(9619) + atc(9619)
			+ "\n" + atc(9794) + "手表\t"+ atc(9794) + "高达\t" + atc(9794) + "二手手机\t"+ atc(9794) + "键盘"
			+ "\n" + "99999999");
		}else if(pp == 2) {
			System.out.print("\t" + atc(9619) + atc(9619) + "热爱美好新时代" + atc(9619) + atc(9619)
			+ "\n" + atc(9794) + "手表\t"+ atc(9794) + "高达\t" + atc(9794) + "二手手机\t"+ atc(9794) + "键盘"
			+ "\n" + "123123123123");
		}

		System.out.println("\n" + "\n" + "\n");
		
		/*
		 * 2021/10/20
		 * 
		 * 
		 */
		String brand = "爱国者F928";
		double weight = 12.4;
		String ptype = "内置锂电池";
		double bprice = 499;
		System.out.println("品牌：\t\t" + brand 
				+ "\n" + "重量：\t\t" + weight
				+ "\n" + "电池类型：\t" + ptype
				+ "\n" + "价格：\t\t" + bprice
				+ "\n");
		
		/*
		 * 我们敬爱的宿舍长爱吃什么？
		 * 随机数，宿舍长的薛定谔的性别
		 */
		String name = "陈洋";
		//char sex = '女';
		String food = "老八秘制小汉堡";
		int pnumber;
		double price = 5.5;
		char sexc = '受';
		
		Random cy = new Random();
		int sex = cy.nextInt(2);
		if(sex==1) {
			sexc = '男';
		}else {
			sexc = '女';
		}
		System.out.println("陈洋今天吃了几个小汉堡？");
		pnumber = number.nextInt();
		price = price * pnumber;
		System.out.println("姓名：" + name + "\n" +"性别：" + sexc + "(薛定谔的性别)"
				+ "\n" + "食物：" + food + "\n" + "数量：" + pnumber 
				+ "\n" +"价格：" + price + "\n");
		//System.out.println(sex);
		
		/*
		 * 将超过24小时的时间转换成天
		 * 
		 */
		int day = 0;
		int hour = number.nextInt();
		int i = 0;
		
		do {
			if(hour>=24){
				day++;
				hour = hour - 24;
				
			}else {
				i++;
			}
		}while(i==0);
		
		System.out.print(day + "天" + hour + "小时" + "\n" + "\n" + "\n");
		
		/*
		 * 
		 * 
		 */
		String xing = "*********";
		double Tcost = 32;
		double Tn = 2;
		double Scost = 27;
		double Sn = 1;
		double Rcost = 30;
		double Rn = 1;
		double pay = 100;
		double discount = 0.8;
		int point = 0;
		int xx = 0;
		
		double cost = (Tcost*Tn + Scost*Sn + Rcost*Rn)*discount;
		double c1 = cost;
		double change = pay - cost;
		
		do {
			if(c1>10) {
				point = point + 3;
				c1 = c1 - 10;
			}else {
				xx++;
			}
		}while(xx==0);
		
		System.out.println("消费总金额：" + cost 
				+ "\n" + xing + atc(655328) + "消费单" + atc(655328) + xing
				+ "\n" + "图书\t" + "单价\t" + "数量\t" + "金额\t"
				+ "\n" + "T恤\t" + atc(655333) + "32\t" + "2\t" + atc(655333) + "64"
				+ "\n" + "网球鞋\t" + atc(655333) + "27\t" + "1\t" + atc(655333) + "27" 
				+ "\n" + "网球拍\t" + atc(655333) + "30\t" + "1\t" + atc(655333) + "30" 
				);
		System.out.print("折扣：\t8折\n" + "消费总金额：\t" + atc(655333) + cost
				+ "\n" + "实际交费：" + atc(655333) + pay
				+ "\n" + "找钱：" + atc(655333) + change
				+ "\n" + "本次购物所获得的积分是：" + point
		);
		
		
		// 读取图片
		BufferedImage bfedimage = ImageIO.read(new File("/home/guest/eclipse-workspace/xjp.jpg"));
		// 图片转字符串后的数组
		char[][] css = new char[bfedimage.getWidth()][bfedimage.getHeight()];
		for (int x = 0; x < bfedimage.getWidth(); x++) {
				for (int y = 0; y < bfedimage.getHeight(); y++) {
					int rgb = bfedimage.getRGB(x, y);
					Color c = new Color(rgb);
					// 得到灰度值
					int cc = (c.getRed() + c.getGreen() + c.getBlue()) / 3;
					css[x][y] = cs[(int) ((cc * 10 - 1) / 255)];
				}
		}
		StringBuffer sb = new StringBuffer();
		// 开始拼接内容
		for (int y = 0; y < css[0].length; y++) {
			for (int x = 0; x < css.length; x++) {
				sb.append(css[x][y]);
			}
			sb.append("\r\n");
		}
		writeFile(new File("/home/guest/eclipse-workspace/1.txt"), sb.toString(), "utf-8");
		//System.out.print(sb);
		number.close();
	}
	/**
	写文件
	@param filewriteFile
	@param string
	字符串
	@param encoding
	编码
	@return 文件大小
	@throws IOException
	*/
	public static int writeFile(File file, String string, String encoding) throws IOException {
		FileOutputStream fos = new FileOutputStream(file);
		try {
			byte[] bs = string.getBytes(encoding);
			fos.write(bs);
			return bs.length;
		} finally {
			fos.close();
		}
	}
}
