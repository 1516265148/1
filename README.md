package sagit;

import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import javax.imageio.ImageIO;
import java.util.Random;
import java.lang.Math;

public class Sagit {
	
	public static char atc(int ascii) {
		char ch =(char)ascii;
		return ch;
	}
	
	/** 此处设置灰度字符，此处只用十个字符，可以设置更多 */
	private static char[] cs = new char[] {'.', ',', '*', '+', '=', '&', '$', '@', '#', ' '};
	public static void main(String[] args) throws IOException {
		
		/*
		 * 我们敬爱的宿舍长爱吃什么？
		 * 随机数，宿舍长的薛定谔的性别
		 */
		String name = "陈洋";
		//char sex = '女';
		String food = "老八秘制小汉堡";
		int number = 1;
		double price = 5.5;
		char sexc = '受';
		
		//Random cy = new Random();
		Random cy = new Random();
		int sex = cy.nextInt(2);
		if(sex==1) {
			sexc = '男';
		}else {
			sexc = '女';
		}
		
		System.out.println("姓名：" + name + "\n" +"性别：" + sexc + "(薛定谔的性别)"
				+ "\n" + "食物：" + food + "\n" + "数量：" + number 
				+ "\n" +"价格：" + price + "\n");
		
		
		/*
		 * 将超过24小时的时间转换成天
		 * 
		 */
		int day = 0;
		int hour = 1320;
		int i = 0;
		
		do {
			if(hour>=24){
				day++;
				hour = hour - 24;
				
			}else {
				i++;
			}
		}while(i==0);
		
		System.out.print(day + "天" + hour + "小时");
		
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
		System.out.print("折扣：\t8折\n" + "消费总金额：\t" + atc(655333) + change
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
