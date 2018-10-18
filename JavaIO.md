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
2. ObjectInputStream
```
public class ObjectInputStream
extends InputStream
implements ObjectInput, ObjectStreamConstants
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
2. ObjectOutputStream
```
public class ObjectOutputStream
extends OutputStream
implements ObjectOutput, ObjectStreamConstants
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
2. BufferedReader
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
