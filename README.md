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

