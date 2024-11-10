# KAGGLE-COMPETITION-DESION-TREE
# Chekish ehtimolini bashorat qilish loyihasi

Ushbu loyiha sog'liq va demografik ma'lumotlarga asoslangan holda chekish ehtimolini bashorat qiladi. Ma'lumotlarni qayta ishlash, xususiyatlarni yaratish va ansambl texnikalaridan foydalaniladi. Bunda qaror daraxtlarini Bagging yordamida va Random Forest tasniflagichidan foydalanib model qurish va takroriy xususiyatlarni tanlash (RFECV) orqali eng muhim xususiyatlarni tanlash amalga oshiriladi.

## MUNDARIJA
- [Loyiha tuzilmasi](#loyiha-tuzilmasi)
- [Xususiyatlarni yaratish](#xususiyatlarni-yaratish)
- [Model yaratish](#model-yaratish)
- [Xususiyatlarni tanlash](#xususiyatlarni-tanlash)
- [Baholash](#baholash)
- [Natijalarni saqlash](#natijalarni-saqlash)

---

## Loyiha tuzilmasi

Loyihada quyidagi fayllar mavjud:
- `train.csv` - O'quv (trening) ma'lumotlari.
- `test.csv` - Maqsad qiymatlari bo'lmagan test ma'lumotlari.
- `sample_submission.csv` - Namunaviy natijalar fayli.
- `my_submission_tuning.csv` - Dastur tomonidan yaratilgan yakuniy natijalar fayli.
- `README.md` - Ushbu hujjat.

---

## Xususiyatlarni yaratish

Xususiyatlarni yaratish jarayonida ma'lumotdagi o'zaro bog'liqliklarni aks ettiruvchi yangi xususiyatlar hosil qilinadi. Quyidagi xususiyatlar yaratildi:

1. **BMI**: Og'irlikni bo'yning kvadratiga bo'lish orqali hisoblangan tana massasi indeksi.
2. **Bo'y-bel nisbati**: Bo'y va belning o'zaro nisbati.
3. **Og'irlik-bel nisbati**: Og'irlik va belning o'zaro nisbati.
4. **Ko'rish farqi**: Chap va o'ng ko'z uchun ko'rish qiymatlarining farqi.
5. **Eshitish farqi**: Chap va o'ng quloq uchun eshitish qiymatlarining farqi.

**GIF Misol**: *Ma'lumotlarda ushbu hisoblarni qanday amalga oshirilishini tasvirlovchi GIF qo'shish foydali bo'ladi.*

---

## Model yaratish

Chekish ehtimolini bashorat qilish uchun ikkita modeldan foydalanildi:
1. **Bagging va qaror daraxti tasniflagichi**: Bagging yordamida qaror daraxti modelining barqarorligi va aniqligi oshirildi.
2. **Random Forest tasniflagichi**: Bir nechta qaror daraxtlarini birlashtirish kuchidan foydalanildi, shuningdek, xususiyatlarni tanlash uchun RFECV usuli qo‘llandi.

### Modellar uchun parametrlar
- **Bagging va qaror daraxti**:
  - `max_depth`: 7
  - `min_samples_leaf`: 0.16
  - `min_impurity_decrease`: 0.005
  - `n_estimators`: 379
- **Random Forest tasniflagichi**:
  - `n_estimators`: 450

**GIF Misol**: *Ansambl usullari, Bagging va Random Forest texnikalari haqida qisqa GIF qo'shish foydali bo'ladi.*

---

## Xususiyatlarni tanlash

**RFECV** yordamida Random Forest modeli eng muhim xususiyatlarni tanlaydi. Bu usul ortiqcha moslashuvni kamaytiradi va modelning umumiylashuvi yaxshilanadi. Tanlangan xususiyatlar asosida Random Forest modeli qayta o‘qitiladi.

**GIF Misol**: *RFECV jarayoni, iteratsiyalarda qanday xususiyatlar tanlanayotganini tasvirlovchi GIF qo‘shish yaxshi natija beradi.*

---

## Baholash

Modellar quyidagi mezonlar yordamida baholanadi:
- **Aniqlik darajasi (Accuracy)**: To'g'ri bashoratlar foizini o'lchaydi.
- **ROC AUC mezoni**: Ijobiy namunalarni salbiylardan yuqori reytingda joylashtirish qobiliyatini baholaydi.

Baholash natijalarining namunasi:
```plaintext
BaggingClassifier Accuracy: 0.8300
BaggingClassifier ROC AUC: 0.7500
Selected features: 10
Random Forest Accuracy: 0.8450
Random Forest ROC AUC: 0.7650
