# 02- Makine Öğrenmesi Algortimalarının Başarılarının Karşılaştırılması

Kullanılan veri setindeki veriler Portekiz bankacılık kurumunun pazarlama kampanyaları ile ilgilidir. Kampanya müşteri adayları ile gerçekleşen telefon konuşmasını ve müşteri bilgilerini içerir. Sınıflandırmanın amacı müşterinin vadeli mevduata abone olup olmayacağı ile ilgilidir. Abonelik bilgileri veri setinde “default” özelliğinde yes/no şeklinde gösterilmiştir. Yani veri setimizdeki bağımlı değişken “default” özelliğidir. 

-Makine öğrenmesi algoritmalarının başarılı  sonuç vermesi için bağımlı değişkenin özelliklerinin yakın oranda dağılması gerekmektedir. Bu dağılmayı anlamak için `print(bankaVeriSeti.deposit.value_counts())` metodu kullanılır.

![Ekran Alıntısı](https://user-images.githubusercontent.com/117931965/227779293-f47b4de4-e1c3-4e13-8561-a7f528cc578d.PNG)

-Makine öğrenmesi algoritmalarının çoğu sayısal veriler ile çalışmaktadır. Bu sebele veri setinde bulunan kategorik veriler, sayısal verilere çevirilmelidir. Verilerin tipini öğrenmek için `bankaVeriSeti.dtypes` metodu kullanılmıştır.

![Ekran Alıntısı](https://user-images.githubusercontent.com/117931965/227781543-23d71640-8868-4b6a-800d-4c4b4ef2bade.PNG)

-Kategorik değerlerin sayısal değerlere çevirilmesi için "dummy" değişkeni kullanılmıştır. Bu işlem tüm kategorik değerler için uygulanmıştır.

```
def encode(x):
	if x == "yes": 
	return 1 
	elif x == "no": 
	return 0 
	else: 
	return 2
bankaVeriSeti["deposit_encode"] = bankaVeriSeti.apply(lambda x: encode(x["deposit"]), axis 
bankaVeriSeti = pd.get_dummies(bankaVeriSeti ,prefix = "deposit" 
                                           ,columns = ["deposit"] 
                                           ,drop_first = True)
```  
Veri setinin son hali aşağıda verilen görselde oludğu gibi tamamen sayıssal hale getirilmiştir.

![Ekran Alıntısı](https://user-images.githubusercontent.com/117931965/227782039-3ca47a75-37d9-450f-b5c3-99afbe82a1e1.PNG)

Veri seti biraz daha incelenmiştir. Ve aşağıda görüldüğü gibi bağımlı değişkenin değerlerinin eşit bir şekilde dağılmadığı görülmüştür. Bu da sınıflandırma için doğru bir veri seti olmadığını gösterir. Çünkü abone olmama yüzdesi çok yüksek. Sınıflandırma zaten hepsine hayır dese bile yüksek başarı oranı elde edilir.

```
count_no_sub = len(bankaVeriSeti[bankaVeriSeti['default_encode']==0])
count_sub = len(bankaVeriSeti[bankaVeriSeti['default_encode']==1])
pct_of_no_sub = count_no_sub/(count_no_sub+count_sub) 
print("abonelik olmamasının yüzdesi ", pct_of_no_sub*100) 
pct_of_sub = count_sub/(count_no_sub+count_sub) 
print("abonelik yüzdesi", pct_of_sub*100)
```

![image](https://user-images.githubusercontent.com/117931965/229936545-0995351c-0fce-431e-985d-80a2e31074cf.png)

Son olarak tüm sınıflandırma yöntemlerinde kullanılmak üzere veri seti “test ve train” olacak şeklinde bölünmüştür. X değişkeni bağımsız, y değişkeni ise bağımlı değişkenleri içermektedir.

```
x=bankaVeriSeti.drop("default_encode", axis=1)
y=bankaVeriSeti["default_encode"]
```

Ardından x ve y değişkenleri test ve train olmak üzere %33’e %77 oranında bölünüyor.
`x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.33, random_state=0)`

**1. Lojistik Regresyon**

Lojistik regresyon sınıflandırma algoritmalarından bir tanesidir. Veri setimizdeki default değerini evet mi, hayır mı? Olduğunu bize gösterecektir. Sınıflandırma yapmak için sigmoid fonksiyonu kullanılır. Sınıflandırma bağımlı ve bağımsız değişken arasında yapılır.

-x_train ve y_train bilgileri fit edilir. Ve yeni bir bir p_pred seti oluşturulur.

```
logr=LogisticRegression(random_state=0)
logr.fit(x_train,y_train) 
y_pred_logr=logr.predict(x_test)
```




