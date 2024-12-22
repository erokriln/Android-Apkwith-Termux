从Termux开始构建应用 

#ApkWith Termux

#基本依赖

1.aapt2 

2.d8 

3.apksigner 

4.keytool 

5.openjdk 

6.android.jar 

#apk 签名文件生成 

keytool -genkey -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias

#apk 签名

apksigner sign --ks my-release-key.jks --ks-key-alias my-key-alias --out signed-app.apk unsigned-app.apk


#资源的编译

aapt2 compile --dir ./res/ -o ./res.zip

#资源连接

aapt2 link -o ./myapp.apk --manifest ./AndroidManifest.xml -I /path/to/android.jar -R ./res.zip

#xml校检

xmllint --noout myfile.xml


#java 文件编译

javac -cp /path/to/dependency1.jar:/path/to/dependency2.jar MyClass.java  # Linux/macOS
javac -cp C:\path\to\dependency1.jar;C:\path\to\dependency2.jar MyClass.java  # Windows


#class打包 

d8 --output ./out --lib /path/to/android.jar ./MyClass.class
d8 --output ./out --classpath ./lib1.jar:./lib2.jar ./MyClass.class


