����j2cache�����������ƿ�����һ�׷ֲ�ʽ���档֧��2����������2���Ķ༶����ϵͳ��

github��ַ��[atoms](https://github.com/zhitongjob/atoms)

�����ļ�
```
<?xml version="1.0" encoding="UTF-8"?>
<atoms>
	<broadcast type="redis" >
		<broadcastConfig host="192.168.1.53" port="6379"/>
	</broadcast>
	<serializer type="fst"/>
	<cache level="1" type="ehcache" delete_atom="true" ><!-- expiredOperator="update" waitTime="100" --><!-- expiredOperator: update,delete  ��ΪupdateʱwaitTime��Ч-->
		<cacheConfig configFile="ehcache.xml"/>
		<cacheTTL>
			<ttl name="hello" value="1000"/><!-- name:regionName value:ʧЧʱ�� ��λ���룩 -->
		</cacheTTL>
	</cache>
	<cache level="2" type="redis">
		<cacheConfig host="192.168.1.53" port="6379" timeout="2000" database="13" namespace="atoms" maxTotal="-1" maxIdle="2000"
		 maxWaitMillis="100" minEvictableIdleTimeMillis="864000000" minIdle="1000" numTestsPerEvictionRun="10" lifo="false"
		 softMinEvictableIdleTimeMillis="10" testOnBorrow="true" testOnReturn="false" testWhileIdle="false" timeBetweenEvictionRunsMillis="300000"
		 blockWhenExhausted="true" password=""/>
		<cacheTTL>
			<ttl name="hello" value="3000"/><!-- name:regionName value:ʧЧʱ�� ��λ���룩 -->
		</cacheTTL>
	</cache>
	<cache level="3" type="redis">
		<cacheConfig host="192.168.1.22" port="6379" timeout="2000" database="13" namespace="atoms" maxTotal="-1" maxIdle="2000"
		 maxWaitMillis="100" minEvictableIdleTimeMillis="864000000" minIdle="1000" numTestsPerEvictionRun="10" lifo="false"
		 softMinEvictableIdleTimeMillis="10" testOnBorrow="true" testOnReturn="false" testWhileIdle="false" timeBetweenEvictionRunsMillis="300000"
		 blockWhenExhausted="true" password=""/>
		 <cacheTTL>
			<ttl name="hello" value="5000"/><!-- name:regionName value:ʧЧʱ�� ��λ���룩 -->
		</cacheTTL>
	</cache>
</atoms>
```

ʹ�ô��룺
``` java
CacheChannel cc=CacheChannel.getInstance();
cc.set("jobell", "hello", "nihaoya");
cc.evict("jobell", "hello");
while(true){
	Object value=cc.get("jobell", "hello");
	if(value==null){
		System.out.println("==============="+value);
	}else{
		System.out.println("==============="+value);
	}
}
```
