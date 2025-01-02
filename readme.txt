5 FARKLI DILDE SES VERISI KAZIMA VE ON ISLEME PROJE 2 README

GitHub proje hesabımı gizli yapıp proje linkini sorunsuz bir şekilde nasıl paylaşabileceğimi bulamadığım için ve bir sorun yaşanmaması adına proje public olarak bırakılmıştır.

Proje Açıklaması

Bu proje, ses verilerini işleyerek konuşma tanıma yapmak amacıyla geliştirilmiştir. Google Colab ortamında çalıştırılmak üzere tasarlanmış olup, veriler Google Drive üzerinden alınmaktadır. Proje, farklı konuşma tanıma modelleri üzerinde eğitim ve değerlendirme yaparak performans analizi sağlar. Eğitim sürecinde çeşitli görselleştirmeler, doğruluk ve kayıp grafikleri, karmaşıklık matrisi ve ROC eğrisi gibi metrikler sunulmaktadır.

Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki kütüphaneler gereklidir:

torch: PyTorch kütüphanesi, derin öğrenme modelleri için kullanılır.
transformers: HuggingFace Transformers kütüphanesi, önceden eğitilmiş modelleri yüklemek için kullanılır.
matplotlib: Görselleştirmeler için kullanılır.
scikit-learn: Değerlendirme metrikleri için kullanılır.
tqdm: Eğitim ve test süreçlerinde ilerleme çubuğu eklemek için kullanılır.

Bu kütüphaneler Google Colab ortamında önceden yüklü olduğundan, herhangi bir ek kurulum gerekmemektedir.

Veri

Veri, Google Drive'dan alınmaktadır. Google Colab ile Google Drive'ı bağladıktan sonra verilerinizi ilgili dizine yerleştirmeniz gerekmektedir.

Veri Yükleme

Veri yüklemek için aşağıdaki kodu kullanabilirsiniz:

from google.colab import drive
drive.mount('/content/drive')

# Verinin bulunduğu dizine erişim
data_path = "/content/drive/MyDrive/veri_dizini/"


Model Eğitimi

Projede, ses tanıma için farklı önceden eğitilmiş modeller kullanılmaktadır. Eğitim işlemi sırasında, her bir model için doğruluk ve kayıp değerleri, karmaşıklık matrisi ve ROC eğrisi gibi metrikler hesaplanır.

Eğitim Fonksiyonu

Modeli eğitmek için aşağıdaki train_model fonksiyonu kullanılmaktadır. Bu fonksiyon, her bir model için eğitim, doğrulama ve erken durdurma (early stopping) işlemlerini içerir.

def train_model(model_name, train_loader, val_loader, device, writer, num_epochs=10, patience=3):
    # Modeli eğitir ve eğitim sürecini loglar

Eğitim sırasında, modelin her epoch sonunda doğruluk ve kayıp grafikleri çizilir. Ayrıca, erken durdurma mekanizması sayesinde modelin eğitim süresi optimize edilir.

Model Değerlendirme

Eğitim tamamlandığında, model test verisi üzerinde değerlendirilir ve aşağıdaki metrikler hesaplanır:

Doğruluk (Accuracy)
Kesinlik (Precision)
Hatırlama (Recall)
Özellik (Specificity)
F1-Score
ROC AUC

def evaluate_model_with_output(model, test_loader, device, model_name):
    # Modeli test verisi üzerinde değerlendirir ve performans metriklerini döndürür

Değerlendirme işlemi sırasında, karmaşıklık matrisi ve ROC eğrisi görselleştirilir.

Sonuçların Görselleştirilmesi

Eğitim ve test süreçlerinde elde edilen sonuçlar görselleştirilir. Aşağıdaki fonksiyonlar, bu metriklerin görsel çıktıları için kullanılır:

Karmaşıklık Matrisi: Modelin tahmin ettiği sınıfların doğruluğunu gösteren bir matris.

ROC Eğrisi: Modelin sınıflar arasındaki doğru tahmin oranlarını gösterir.

Eğitim ve Doğrulama Kayıp ve Doğruluk Grafikleri: Modelin eğitim sürecinde kayıp ve doğruluk değerlerinin görselleştirilmesi.

def plot_confusion_matrix(conf_matrix, model_name, subdirectories):
    # Karmaşıklık matrisini görselleştirir

def plot_roc_curve(y_true, y_pred_prob, model_name, subdirectories):
    # ROC eğrisini ve AUC değerlerini görselleştirir

def plot_training_metrics(training_history, model_name):
    # Eğitim sırasında kaydedilen loss ve doğruluk değerlerini görselleştirir

Çalıştırma

Projeyi çalıştırmak için aşağıdaki adımları takip edebilirsiniz:

1) Google Colab'da yeni bir notebook oluşturun.
2) Google Drive'ınızı bağlayın ve veri dizininizi yükleyin.
3) Yukarıda belirtilen kütüphanelerin önceden yüklü olduğunu doğrulayın.
4) Kod hücrelerini sırayla çalıştırarak modelinizi eğitin ve değerlendirin.

 

DOĞUKAN.
