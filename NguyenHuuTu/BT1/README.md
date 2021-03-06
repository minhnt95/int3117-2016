#**Bài tập tuần 4**
* Độ bao phủ: Sử dụng Tool EclEmma Java Code Coverage 2.x.x (Eclipse Tool)
* Kết quả:
	* Detail:
		![Coverage](https://github.com/ducanhk58uet/int3117-2016/blob/master/NguyenHuuTu/BT1/img/Coverage.png?raw=true)
	* Code:   
		![Co_inCode](https://github.com/ducanhk58uet/int3117-2016/blob/master/NguyenHuuTu/BT1/img/Co_inCode.png?raw=true)
	* Đồ thị: sử dụng code2flow.com
		![Flow](https://github.com/ducanhk58uet/int3117-2016/blob/master/NguyenHuuTu/BT1/img/Flow.png?raw=true)

#**Bài tập tuần 3**
* Nâng cấp test cases của tuần 1

##**Mô tả bài toán**
* Bài toán: Tìm ước chung lớn nhất UCLN của 2 số phương thức: UCLN(a,b);
* Phương pháp kiểm thử: Lớp tương đương
* Phân thành các lớp và các testcase:
	* Cận dưới: a=0, b=0;
	* Cận trên: a=32767, b=32767;
	* Giá trị 1: a=1, b=327;
	* Số nguyên tố: a=13, b=29;
	* Một cặp bất kì: a=100, b=80;
	* Giá trị âm a=-10, b=-100;
* Chọn phương pháp Lớp tương đương, thì chúng ta có thể kiểm soát các giá trị nhập vào, giá trị đặc biệt, tức là trong đó nó đã bao gồm phương pháp biên Bài toán này với kiểu dữ liệu int chúng ta có thể xử lí các giá trị từ 0->32767

##**Test cases**
* Cận dưới: a=0, b=0;
````java
   @Test
    public void test00UCLN() {
        int a = 0;
        int b = 0;
        assertFalse(a>0);
        assertFalse(b>0);
    }
```

* Cận trên:
```java
    @Test
    public void test01UCLN() {
        int a = 32768;
        int b = 32768;
        assertFalse(a<=32767);
        assertFalse(b<=32767);
    }

    @Test
    public void test02UCLN() {
        int a = 32767;
        int b = 32767;
        int expResult = 32767;
        int result = BT1.UCLN(a, b);
        assertTrue(expResult==result);
    }
```

* Một cặp bất kì: a=100, b=80;
```java	
    @Test
    public void test03UCLN() {
        int a = 100;
        int b = 80;
        int expResult = 20;
        int result = BT1.UCLN(a, b);
        assertTrue(expResult==result);
    }
```

* Giá trị 1: a=1, b=327;
```java    
    @Test
    public void test04UCLN() {
        int a = 1;
        int b = 327;
        int expResult = 1;
        int result = BT1.UCLN(a, b);
        assertTrue(expResult==result);
    }
```
* Số nguyên tố: a=13, b=29;
```java
    @Test
    public void test05UCLN() {
        int a = 13;
        int b = 29;
        int expResult = 1;
        int result = BT1.UCLN(a, b);
        assertTrue(expResult==result);
    }
```
* Giá trị âm a=-10, b=-100;
```java    
    @Test
    public void test06UCLN() {
        int a = -10;
        int b = -100;
        assertFalse(a>0);
        assertFalse(b>0);
    } 
````

#**Bài tập tuần 1**
* Chương trình Java, sử dụng JUnit Test.

##**Mô tả bài toán**
* Yêu cầu: Tìm ước chung lớn nhất của 2 số cho trước.
* Giải pháp: sử dụng cách thức trừ dần 2 số với nhau cho đến khi 2 số không giảm

##**Hàm chức năng**
```java
public class BT1 {
 
	public static int UCLN(int a, int b){

		while(a!=b){
            
			if(a==0||b==0)return 0;
            
			if(a>b){ 
				a=a-b;
            			}else{
                				b=b-a;
            			}
        		}
        
		return a;
	}
}
```
##**Test cases**
```java
@Test
    public void testUCLN() {
        int a = 0;
        int b = 0;
        assertFalse(a>0);
        assertFalse(b>0);
    }
    
    @Test
    public void test1UCLN() {
        int a = 32768;
        int b = 32768;
        assertFalse(a<=32767);
        assertFalse(b<=32767);
    }

    @Test
    public void test2UCLN() {
        int a = 200;
        int b = 80;
        int expResult = 40;
        int result = BT1.UCLN(a, b);
        assertTrue(expResult==result);
    }
```