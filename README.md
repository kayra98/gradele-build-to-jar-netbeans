GRADELE NETBEANS PROJESİNİ JAR HALİNDE AÇILABİLİR HALE GETİRME


İLK ÖNCELİKLE NETBEANSE DE PROJEDE BUİLD.GRADELE DOSYASINI AÇIN VE EN ALT KISMA 
//İLK ÖNCELİKLE NETBEANSE DE PROJEDE BUİLD.GRADELE DOSYASINI AÇIN VE EN ALT KISMA 
task fatJar(type: Jar) {
    archiveClassifier.set('all') // 'all' adında bir sınıf tanımlar

    // Derlenmiş sınıfları ve bağımlılıkları ekler
    from sourceSets.main.output
    dependsOn configurations.runtimeClasspath

    // Bağımlılıkları ekler
    from { configurations.runtimeClasspath.collect { it.isDirectory() ? it : zipTree(it) } }

    // Çakışan dosyaları dışla
    duplicatesStrategy = DuplicatesStrategy.EXCLUDE

    // Manifest'e ana sınıfı ekle
    manifest {
        attributes(
            'Main-Class': 'com.example.aıds.App' // Ana sınıfın tam adı
        )
    }
}


BUNU YAZIN VE MAİN CLASS KISMINA KENDİ MAİN CLASINIZI YAZIN

VE BU KODU BU ŞEKİLDE KAYDEDİN 
ARDINDAN PROJENİZİN OLDUĞU DOSYADA CMD İSTEMCİSİNİ AÇIN VE gradlew fatJar YAZIN VE ÇALIŞTIRIN OTOMATİK OLARAK BUİLDLENCEK VE BAĞIMLILILARDA İÇİNE EKLNCEKTİR 
