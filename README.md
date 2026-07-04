# Z.eSystem Plus 2

## Yenilikler:
1. Dosya sistemi geldi
2. Scrolling yapılabilir
3. Dosya kaydetme, yükleme ve silme gelmiştir
4. Artık sistem kalıcı diske kurulabilir

## Gereksinimler:
* RAM: 120MB veya üstü(Önerilir)
* Disk: IDE
* Depolama: 10MB veya üstü(önerilir)

### Nasıl kurulur:

#### Bölüm 1: Disk oluşturma

Önce disk oluşturuyoruz.

```bash
qemu-img  create -f raw hdd.img 10M
```

#### Bölüm 2: Sistemi kurma

Sonra kurulum medyasını çalıştırın.

```bash
qemu-system-i386 -drive file=hdd.img,format=raw,if=none,id=drive-hdd -device ide-hd,bus=ide.0,unit=0,drive=drive-hdd -drive file=os.img,format=raw,if=none,id=drive-os -device ide-hd,bus=ide.0,unit=1,drive=drive-os,bootindex=1
```

Ondan sonra karşınıza bir QEMU penceresi çıkacaktır ve şöyle görünecektir:

```text
PCI OK!
PCI Controller OK!
Kaydedilme basarili!
Icerik: Merhaba ESFS
Yukleme basarili!
Silme basarili oldu!
Z.eSystem Plus'a hosgeldiniz!
Yardim almak icin 'help' yazin.
```

Z.eSystem açıldıktan sonra şu komutu girin:
```text
> install
```

Kurduktan sonra şu komutu girin:
```text
> shutdown
```

#### Bölüm 3: Kurulum sonu:

Kapttıktan sonra şöyle çalıştırın:
```bash
qemu-system-i386 -drive file=hdd.img,format=raw,index=0,media=disk
```

Artık Z.eSystem'ı kullanabilirsiniz!


__NOT:__ AHCI Z.eSystem Plus 3'te gelecektir. Eğer Z.eSystem kaynak kodunu kallanacaksanız MPL 2.0 lisansına uyun.
