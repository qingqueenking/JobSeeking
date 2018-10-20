# *I. java.io*
## File
An abstract representation of file and directory pathnames.
```
public class File
extends Object
implements Serializable, Comparable<File>
```
```
File(String pathname)
```
## InputStream
This abstract class is the superclass of all classes representing an input stream of _**bytes**_.
```
public abstract class InputStream
extends Object
implements Closeable
```
1. FileInputStream
```
public class FileInputStream
extends InputStream
```
```
FileInputStream(File file)
FileInputStream(String name)
```
2. ObjectInputStream
```
public class ObjectInputStream
extends InputStream
implements ObjectInput, ObjectStreamConstants
```
```
ObjectInputStream()
ObjectInputStream(InputStream in)
```
3. FilterInputStream
```
public class FilterInputStream
extends InputStream
```
```
FilterInputStream(InputStream in)
```
4. BufferedInputStream
```
public class BufferedInputStream
extends FilterInputStream
```
```
BufferedInputStream(InputStream in)
```
## OutputStream
This abstract class is the superclass of all classes representing an output stream of _**bytes**_.
```
public abstract class OutputStream
extends Object
implements Closeable, Flushable
```
1. FileOutputStream
```
public class FileOutputStream
extends OutputStream
```
```
FileOutputStream(File file)
FileOutputStream(OutputStream out)
```
2. ObjectOutputStream
```
public class ObjectOutputStream
extends OutputStream
implements ObjectOutput, ObjectStreamConstants
```
```
ObjectOutputStream()
ObjectOutputStream(OutputStream out)
```
## Reader
Abstract class for reading _**character**_ streams.
```
public abstract class Reader
extends Object
implements Readable, Closeable
```
1. InputStreamReader
```
public class InputStreamReader
extends Reader
```
```
InputStreamReader(InputStream in)
```
2. FileReader
```
public class FileReader
extends InputStreamReader
```
```
FileReader(File file)
FileReader(String name)
```
3. BufferedReader
```
public class BufferedReader
extends Reader
```
```
BufferedReader(Reader in)
```
## Writer
Abstract class for writing to _**character**_ streams.
```
public abstract class Writer
extends Object
implements Appendable, Closeable, Flushable
```
1. PrintWriter
```
public class PrintWriter
extends Writer
```
```
PrintWriter(OutputStream out)
```
## Java I/O Design Pattern
装饰器模式，以InputStream为例，InputStream为抽象组件，FileInputStream是InputStream的子类，属于具体组件，装饰者用于装饰组件。
## Java编码
Java使用Unicode编码，这不是说Java不支持其他编码方式，而是说char类型使用Unicode编码。
char类型占两个字节，Unicode中文和英文都占两个字节，这意味着一个char既可以装一个中文也可以装一个英文。
## Character & Bytes
```
String(byte[] bytes)
String(byte[] bytes, Charset charset)
void byte[] getBytes()
void byte[] getBytes(Charset charset)
```
## Serialization & Deserialization
1. Serialization
2. Deserialization
## TCP (java.io.ServerSocket & java.io.Socket)
## UDP (java.io.DatagramSocket & java.io.DatagramPacket)
# *II. java.nio*
The central abstractions of the NIO APIs are:
* Buffers, which are containers for data;
* Charsets and their associated decoders and encoders, which translate between bytes and Unicode characters;
* Channels of various types, which represent connections to entities capable of performing I/O operations;
* Selectors and selection keys, which together with selectable channels define a multiplexed, non-blocking I/O facility.
1. Buffer <br>
A container for data of a specific non-boolean primitive type.
```
public abstract class Buffer
extends Object
```
## Synchronization, Asynchronization, Blocking, Nonblocking
1. Synchronization <br>
烧开水 + 静等/轮询查看
2. Asynchronization <br>
烧开水 + 响铃通知
3. Blocking <br>
烧开水 + 旁边静等（“挂起”）
4. Nonblocking <br>
烧开水 + 打游戏去
## java.nio.ServerSocketChannel & java.nio.SocketChannel
## java.nio.AsynchronousServerSocketChannel & java.nio.AsynchronousSocketChannel
