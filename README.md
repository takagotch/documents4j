### documents4j
---
https://github.com/documents4j/documents4j

http://documents4j.com/#/

```java
File wordFile = new File( ... ), target = new File( ... );
IConverter converter = ... ;
Future<Boolean> conversion = converter
  .convert(wordFile).as(DocumentType.MS_WORD)
  .to(target).as(DocumentType.PDF)
  .prioritizeWith(1000)
  .schedule();

IOConverter converter = LocalConverter.builder()
  .baseFolder(new File("C:\Users\documents4j\temp"));
  .workerPool(20,25, 2, TimeUnit.SECONDS)
  .processTimeout(5, TimeUnit.SECONDS)
  .build();
  

IConverter converter = RemoteConverter.builder()
  .baseFolder(new File("C:\Users\documents4j\temp"));
  .workerPool(20, 25, 2, TimeUnit.SECONDS)
  .requestTimeout(10, TimeUnit.SECONDS)
  .baseUri("http://localhost:9998");
  .build();

IConverter first = ..., second = ...,
IConverterFailureCallback converterFailureCallback = ... ;
ISelectionStrategy selectionStrategy = ...;
IAggregatingConverter converter = AggregatingConverter.builder(0
  .aggregates(first, second)
  .selectionStrategy(selectionStrategy)
  .callback(converterFailureCallback)
  .build();
```

```sh
cd documents4j
cd documents4j-local-demo
mvn jetty:run
java -jar documents4j-server-standalone-shaded.jar http://localhost:9998
java -jar documents4j-client-standalone-shaded.jar http://localhost:9998
taskkill /F /FI "WindowTitle eq Microsoft Word"
taskkill /F /FI "WindowTitle eq Microsoft Office*"
taskill /f /t /im wscript.exe
taskkill /f /t /im winword.exe
mvn package -Pms-office
```

```
```
