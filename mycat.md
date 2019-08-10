
## mycat

#### :dvd: 几个问题
 - mycat能做什么
 - 逻辑表&逻辑库，优点？
 - mod水平切分，其他手段？
 - 垂直切分？
 - 自动处理切分？策略？
 - 父子关系，外键关联关系，相当于垂直切分，ER表
 - mycat有什么缺点

#### :dvd: 垂直切分
按业务规划细分
不缩表，减少字段数

#### :dvd: 水平切分&规则
缩表，减少记录数
1. 枚举法：
   通过在配置文件中配置可能的枚举id，自己配置分片，适用于按照省份或者区县来拆分数据类业务

   ```
  <rule>
  <columns>province_id</columns>
  <algorithm>enum-int</algorithm>
  </rule>
   ```
2. 固定分片hash算法
```
  <tableRule name="rule1">
      <rule>
        <columns>user_id</columns>
        <algorithm>func1</algorithm>
      </rule>
  </tableRule>
  <function name="func1" class="org.opencloudb.route.function.PartitionByLong">
    <property name="partitionCount">2,1</property>
    <property name="partitionLength">256,512</property>
  </function>

  本例的分区策略：希望将数据水平分成3份，前两份各占25%，第三份占50%。（故本例非均匀分区）
  |<---------------------1024------------------------>|
  |<----256--->|<----256--->|<----------512---------->|
  | partition0 | partition1 | partition2 |
```
3. 范围约定
  预先制定可能的id范围到某个分片
  ```
  <tableRule name="auto-sharding-long">
      <rule>
        <columns>user_id</columns>
        <algorithm>rang-long</algorithm>
      </rule>
  </tableRule>
  ```

4. 求模法
  ```
      <columns>user_id</columns>
      <algorithm>mod-long</algorithm>
  ```
5. 日期列分区法
   起始时间
   分区时间间隔

6. 通配取模 
7. ASCII码求模通配
   %n值分n个分区

8. 编程指定
   自定义算法

9. 字符串拆分hash解析
10. 一致性hash

### :dvd: 附图
![img](imgs/db/1508220824685.png) <br><br><br>
![img](imgs/db/1508224104762.png) <br><br><br>
![img](imgs/db/1508224116977.png) <br><br><br>
![img](imgs/db/1508224133068.png) <br><br><br>
![img](imgs/db/1508224143652.png) <br><br><br>
![img](imgs/db/1508224155090.png) <br><br><br>
![img](imgs/db/1508224163862.png) <br><br><br>
![img](imgs/db/1508224175479.png) <br><br><br>
![img](imgs/db/1508224183405.png) <br><br><br>
![img](imgs/db/1508224195432.png) <br><br><br>
![img](imgs/db/1508232831054.png) <br><br><br>
![img](imgs/db/1508233065722.png) <br><br><br>
![img](imgs/db/1508233301178.png) <br><br><br>
![img](imgs/db/1508234022148.png) <br><br><br>
![img](imgs/db/1508234196383.png) <br><br><br>
![img](imgs/db/1508234209931.png) <br><br><br>
![img](imgs/db/1508234224944.png) <br><br><br>
![img](imgs/db/1508234232978.png) <br><br><br>
![img](imgs/db/1508234240747.png) <br><br><br>
![img](imgs/db/1508234256389.png) <br><br><br>
![img](imgs/db/1508234267301.png) <br><br><br>
![img](imgs/db/1508234279553.png) <br><br><br>
![img](imgs/db/1508234313005.png) <br><br><br>
![img](imgs/db/1508234321343.png) <br><br><br>
![img](imgs/db/1508234483676.png) <br><br><br>
![img](imgs/db/1508234508872.png) <br><br><br>
![img](imgs/db/1508234525067.png) <br><br><br>
![img](imgs/db/1508234545534.png) <br><br><br>
![img](imgs/db/1508234554521.png) <br><br><br>


