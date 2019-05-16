# Java相关

## 1.枚举
### 1）枚举 switchcase 标签必须为枚举常量的非限定名称
case语句中只能写枚举类定义的变量名称，不能加类名。正常代码如下
  
	`private void TestEnum(ColorType type){  
       switch (type){  
           case GREEN:  
               break;  
           case RED:  
               break;  
           case ORANGE:  
               break;  
           case WHITE:  
               break;  
           case BLACK:  
               break;  
           default:  

      }  
}`

