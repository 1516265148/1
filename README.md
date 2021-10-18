import java.awt.Color;

import java.awt.image.BufferedImage;

import java.io.File;

import java.io.FileOutputStream;

import java.io.IOException;

 

import javax.imageio.ImageIO;

public class aa {

/** 此处设置灰度字符，此处只用十个字符，可以设置更多 */

private static char[] cs = new char[] {'.', ',', '*', '+', '=', '&', '$', '@', '#', ' '};

public static void main(String[] args) throws IOException {

// 读取图片

BufferedImage bfedimage = ImageIO.read(new File("D:\\pikaqiu1.jpg"));

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

writeFile(new File("D:\\content1.txt"), sb.toString(), "utf-8");

}

/**

* 写文件

*

* @param file

* @param string

* 字符串

* @param encoding

* 编码

* @return 文件大小

* @throws IOException

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
