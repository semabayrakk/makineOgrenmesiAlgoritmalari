# 02- Makine Öğrenmesi Algortimalarının Başarılarının Karşılaştırılması

Kullanılan veri setindeki veriler Portekiz bankacılık kurumunun pazarlama kampanyaları ile ilgilidir. Kampanya müşteri adayları ile gerçekleşen telefon konuşmasını ve müşteri bilgilerini içerir. Sınıflandırmanın amacı müşterinin vadeli mevduata abone olup olmayacağı ile ilgilidir. Abonelik bilgileri veri setinde “default” özelliğinde yes/no şeklinde gösterilmiştir. Yani veri setimizdeki bağımlı değişken “default” özelliğidir. 

-Makine öğrenmesi algoritmalarının başarılı  sonuç vermesi için bağımlı değişkenin özelliklerinin yakın oranda dağılması gerekmektedir. Bu dağılmayı anlamak için `print(bankaVeriSeti.deposit.value_counts())` metodu kullanılır.

![Ekran Alıntısı](https://user-images.githubusercontent.com/117931965/227779293-f47b4de4-e1c3-4e13-8561-a7f528cc578d.PNG)

-Makine öğrenmesi algoritmalarının çoğu sayısal veriler ile çalışmaktadır. Bu sebele veri setinde bulunan kategorik veriler, sayısal verilere çevirilmelidir. Verilerin tipini öğrenmek için `bankaVeriSeti.dtypes` metodu kullanılmıştır.

