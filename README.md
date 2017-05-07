public class Client{
public static void main(String args[])
{		//动态确定套餐种类	    
MealBuilder mb=(MealBuilder)XMLUtil.getBean();	
//服务员是指挥者	
KFCWaiter waiter=new KFCWaiter();	  
//服务员准备套餐	   
waiter.setMealBuilder(mb);	    //客户获得套餐	
Meal meal=waiter.construct();          
System.out.println("套餐组成：");     
System.out.println(meal.getFood());     
System.out.println(meal.getDrink());	
}}
public class KFCWaiter{
private MealBuilder mb;	
public void setMealBuilder(MealBuilder mb)	
{	
this.mb=mb;	
}	
public Meal construct()	{	
mb.buildFood();	
mb.buildDrink();	
return mb.getMeal();
}}
public class Meal{	
//food和drink是部件	private String food;	
private String drink;		
public void setFood(String food) {		
this.food = food; 
}	
public void setDrink(String drink) {	
this.drink = drink; 
}
public String getFood() {		
return (this.food); 
}	
public String getDrink() {	
return (this.drink); 
}}
public abstract class MealBuilder{	
protected Meal meal=new Meal();
public abstract void buildFood();	
public abstract void buildDrink();
public Meal getMeal()	{		
return meal;	
}}public class SubMealBuilderA extends MealBuilder{
public void buildFood()	{	
meal.setFood("一个汉堡");	
}	
public void buildDrink()	{	   
meal.setDrink("一杯开水");	
}}
public class SubMealBuilderB extends MealBuilder{	
public void buildFood()	{	
meal.setFood("一个鸡腿");	}	
public void buildDrink()	{		
meal.setDrink("一杯可乐");
}}
