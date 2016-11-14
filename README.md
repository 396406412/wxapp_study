## ǰ��
>������С�����Ƴ�����֮�󣬺ܶ�С��鶼�Ѿ�ץ������ע��С�����ˡ��ڿ����׶���Ҳ�����˺ܶ�����⣬����`wx.request`�������󲻳ɹ������������ʱ����֪�������������push���ݣ�input��μ����û������״̬��css��background-image�޷���ȡ������Դ�ȵȣ������ͻ��һ��ר�⣬��������Щ�����С�����˼·��

## �������
����������Ҫ�����ǣ����������
���Ŷ����ù�vuejs��reactjs��mvvm��ܵ�ͯЬ��΢��С���������������Եúܼ�����ԭ����һ���ġ�

![''](http://lanchenglv.com//uploads/images/20161113222748.jpg)

![''](http://lanchenglv.com//uploads/images/20161113233447.jpg)


���Ǽ�����һ��demo���Ѿ��ϴ���github����ʱ������ֱ�����ء�������Ҫ���������г��õ�һЩ������������������ǰ�������µ����ݡ��޸����顢ɾ�����顢������飬������һЩ������ʽ���һ�����ѧϰ˼·��

demo��ַ��
https://github.com/bluefox1688/wxapp_study

demo�������������·����
`/pages/array/array.wxml`

 
### ��ǰ�������µ�����

``` stylus

Page({
  data: {
   	 list:[{
		id:1,
		name:'Ӧ���ʹ�',
		count:1
   	 },{
		id:2,
		name:'���¸��',
		count:6
   	 },{
		id:3,
		name:'ȫ����ʳ����ԭ��',
		count:12
   	 },{
		id:4,
		name:'�����������ͺ���',
		count:5
   	 }]
  }
})

```
���ǳ�ʼ��һЩ���ݣ�������Ҫ��list������µ��������Ҫ�õ�`JavaScript concat()`�ķ�����`concat()` �����������������������飬�÷�������ı����е����顣
��ʵ���ǵ���˵����ǰ���������ݣ���ʵҲ���ǰ����������ƴ���������һ���µ����飬Ȼ����ʹ��`this.setData()`������Ⱦ��ҳ���ϡ�
���ǿ�һ����΢��С������Ĵ��롣

**��ǰ��������demo**
``` stylus

 //��ǰ��������
  add_before:function (){

  
//Ҫ���ӵ�����
var newarray = [{
	id:6,
	name:'��ǰ��������--'+new Date().getTime() ,
	count:89
}];
  	
//ʹ��concat()�������������ƴ����
this.data.list = newarray.concat(this.data.list);
	
//����ƴ֮������ݣ����͵���ͼ�㣬����Ⱦҳ��
//������¼���޸������ݺ�һ��Ҫ�ٴ�ִ��`this.setData()`��ҳ��Ż���Ⱦ���ݵġ�
this.setData({
  	'list':	this.data.list
 });
  	
  	
  }
```

**����������demo**
``` stylus

  //�����������
  add_after:function (){

	//Ҫ���ӵ�����
	var newarray = [{
			id:5,
			name:'�����������--'+new Date().getTime() ,
			count:89
	}];
	

	this.setData({
		'list':this.data.list.concat(newarray)
	});
  	
  	
  },
```
ϸ�ĵ�С���Ӧ�ûᷢ�֣�����������`concat()`��ƴ����ʱ��concat������������ǲ�һ���ġ���ǰ���������ݵ�������������ˡ�

``` stylus

//������һ��������Ҫ����������
var newarray = [{
		id:5,
		name:'�����������--'+new Date().getTime() ,
		count:89
}];

//��ǰ--��newarray��this.data.list��ƴ
this.data.list = newarray.concat(this.data.list);

//���--��this.data.list��newarray��ƴ
this.data.list = this.data.list.concat(newarray);

```

### �޸�����

��չʾ�����ݽ����޸ģ��ڿ��������ǳ����ò��ڳ�������������

``` stylus
  //�޸�����
  edit:function (e){
  	
//���������e���ľ������ã���ο�΢��С����ٷ��ṩ��˵������ַΪhttps://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html?t=20161107
    
var dataset = e.target.dataset;
var Index = dataset.index; //��ͨ����wxmlҳ����ʹ�� data-index="{{index}}"���ݹ����ģ���Ϊʶ�����ڱ༭�޸��ĸ����顣
  	
//����Ҫ�޸ĵ�����
this.data.list[Index].name = '�޸�������'+new Date().getTime();
  	
//����ƴ֮������ݣ����͵���ͼ�㣬����Ⱦҳ��
//������¼���޸������ݺ�һ��Ҫ�ٴ�ִ��`this.setData()`��ҳ��Ż���Ⱦ���ݵġ�
this.setData({
	list:this.data.list
});
  	
  	
  	
  }
```

### ɾ��ĳ������

�����и�Ҳ����ɾ��
ɾ����Ҫ�õ�`JavaScript splice() `��ʽ��`splice() ` ������/�����������/ɾ����Ŀ��Ȼ�󷵻ر�ɾ������Ŀ��

``` stylus

//ɾ��
  remove:function (e){
  	
	var dataset = e.target.dataset;
	var Index = dataset.index;
	
	//ͨ��`index`ʶ��Ҫɾ���ڼ������ݣ��ڶ�������ΪҪɾ������Ŀ������ͨ��Ϊ1
	this.data.list.splice(Index,1);
	
	//��Ⱦ����
	this.setData({
		list:this.data.list
	});
  	
  	
  }

```

### �������

����ɾ֮�󣬻�������һ���������ѽ��

``` stylus
//���
  clear:function (){
  	
    //��ʵ������������һ�������鼴��
  	this.setData({
  		list:{}
  	});
  	
  } 
```

### �ܽ�
����������Ҫ��������ɾ��գ���ʵ������Ĳ������кܶ෽ʽ�ģ����Կ����½�ͼ��

![''](http://lanchenglv.com//uploads/images/20161113232801.jpg)

�����ÿһ���Ĳ�������������ȥ���ڵ�w3s��ѧϰ�¡�
http://www.w3school.com.cn/jsref/jsref_splice.asp

demo��ַ��
https://github.com/bluefox1688/wxapp_study

## ����

![''](http://lanchenglv.com/uploads/images/20161113233806.jpg)

�����Ҷ�΢��С���򿪷�������ǣ���ʶ�˲��ٶ�΢��С������������ţ�ˣ�Ҳ��һЩ�����е����֣��ش��ҽ�����һ��΢��С����������Ȧ�ӣ�ϣ���������һ������ļ�������Ȧ�ӣ������������������ҡ�����Ҳ�᲻���ڷ���һЩ΢��С�����ѧϰ�̡̳�
��Ⱥ��Ŀ��Ϊ�����ɣ����������ļ�������Ⱥ�������ڹ��֮�У��ѿ�����Ⱥ������ȷ�ϻ��ƣ���Ҫ��Ⱥ��С��飬����ҵĸ���΢��`amwhuang`������ע��С������Ⱥ��

>�����׷���ַ��
>�������--΢��С����ѧϰ�̳�
>http://lanchenglv.com/article/2016/1113/wxapp_array_concat_splice.html
>����ת�أ������ת�س�����лл��


