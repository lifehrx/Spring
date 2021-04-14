
#### Spring 的内置缓存@Cacheable
##### 1. 使用方法：在service层加入注解(可以加在类上也可以加在方法上)

```SQL
@Cacheable(value = "cacheWeldingAndHeatDetailStatisticExportList", key = "#cacheString")
```

##### 2. 注意a： value要唯一，key必须是字符串且可唯一确定缓存内容(例如：分页条件要转化为String，后面还追加了查询条件)

```java
@Cacheable(value = "cacheGetPageWeldNumDetail", key ="T(String).valueOf(#currentPage).concat('-').concat(T(String).valueOf(#pageRecords)).concat(#cacheString)")
```

##### 3. 注意b： 映射的实体类要实现 java.io.Serializable 接口，否则会报错。
```java
public class WeldingAndHeatDetailStatistic implements Serializable {
    private String id;
}
```

##### 4. 注意c： 导出报表功能要把写入报表的逻辑和缓存List的逻辑分开写成两个方法，否则会报错。
```java

```
