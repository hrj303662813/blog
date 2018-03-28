# 使用Gson解析Json数组遇到的泛型类型擦除问题解决方法

Sinnce `gson 2.8.0`, you can use `TypeToken#getParametized((Type rawType, Type... typeArguments))` to create the typeToken,   
then getType() should do the trick.  
For example:  
```java
TypeToken.getParameterized(ArrayList.class, myClass).getType();
```


# 使用Jsonson解析Json数组遇到的泛型类型擦除问题解决方法
```java
public static JavaType getCollectionType(Class<?> collectionClass, Class<?>... elementClasses) {   
    return mapper.getTypeFactory().constructParametricType(collectionClass, elementClasses);   
}
```
