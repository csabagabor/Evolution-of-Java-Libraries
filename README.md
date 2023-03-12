# Evolution of Java Libraries
- know exactly which version contains which methods, in which version a particular method is
getting deprecated, when it is being removed etc. (only public methods from public classes)
- contains information about the most widely used ~1000 Maven libraries + the Java standard
library (from Java 8 until Java 19)
- utility used for parsing https://github.com/csabagabor/Jar-Parser-Utility

# Format of the files
- name of the file: `groupId&artifactId.txt` (for the Java standard libraries it is `java&java.txt`)
- inside the file:
  - `###` indicates class
  - `#` indicates method
  - `@` indicates version
  - `+` "introduced"
  - `-` "removed"
  - `*` changed (e.g. `*#<init>(Z)V[deprecated]` indicating that the method is being deprecated in that version)

# Example for the Java standard library (Java 8-19): `java&java.txt`:
```
+###java/util/List
@8
+#size()I
+#isEmpty()Z
+#contains(Ljava/lang/Object;)Z
+#iterator()Ljava/util/Iterator;
+#toArray()[Ljava/lang/Object;
+#toArray([Ljava/lang/Object;)[Ljava/lang/Object;
+#add(Ljava/lang/Object;)Z
+#remove(Ljava/lang/Object;)Z
+#containsAll(Ljava/util/Collection;)Z
+#addAll(Ljava/util/Collection;)Z
+#addAll(ILjava/util/Collection;)Z
+#removeAll(Ljava/util/Collection;)Z
+#retainAll(Ljava/util/Collection;)Z
+#replaceAll(Ljava/util/function/UnaryOperator;)V
+#sort(Ljava/util/Comparator;)V
+#clear()V
+#equals(Ljava/lang/Object;)Z
+#hashCode()I
+#get(I)Ljava/lang/Object;
+#set(ILjava/lang/Object;)Ljava/lang/Object;
+#add(ILjava/lang/Object;)V
+#remove(I)Ljava/lang/Object;
+#indexOf(Ljava/lang/Object;)I
+#lastIndexOf(Ljava/lang/Object;)I
+#listIterator()Ljava/util/ListIterator;
+#listIterator(I)Ljava/util/ListIterator;
+#subList(II)Ljava/util/List;
+#spliterator()Ljava/util/Spliterator;
@9
+#of()Ljava/util/List;
+#of(Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of(Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;Ljava/lang/Object;)Ljava/util/List;
+#of([Ljava/lang/Object;)Ljava/util/List;
@10
+#copyOf(Ljava/util/Collection;)Ljava/util/List;
```


Explanation: 
- `java/util/List` introduced in version 8 (we only go back to Java 8 for simplicity but for Maven libraries all versions are taken into account)
- methods `size()I`, `isEmpty()Z`,...,`spliterator()Ljava/util/Spliterator` are introduced in version 8
- methods `of()Ljava/util/List`, `of(Ljava/lang/Object;)Ljava/util/List`,... are introduced in version 9
- method `copyOf(Ljava/util/Collection;)Ljava/util/List` introduced in version 10

# Example for Mockito Core: `org.mockito&mockito-core.txt`:
```
+###org/mockito/Matchers
@1.3
+#<init>()V
+#anyBoolean()Z
+#anyByte()B
+#anyChar()C
...
@2.0.83-beta
*#anyVararg()Ljava/lang/Object;[deprecated]
...
@2.0.85-beta
-#anyVararg()Ljava/lang/Object;[deprecated]
...
@4.0.0
-###org/mockito/Matchers
```

Explanation:
- class `org/mockito/Matchers` introduced in version 1.3 with methods `<init>()V`,...,`anyChar()C`
- `anyVararg()Ljava/lang/Object;` being deprecated in version `2.0.83-beta`
- `anyVararg()Ljava/lang/Object;` being removed in version `2.0.85-beta`
- class `org/mockito/Matchers` being removed in version `4.0.0`

# Most used Maven libraries - TOP 100
- analysis done by parsing all Java repositories on Github having more than 140 stars

![2](https://user-images.githubusercontent.com/37183688/224573390-f9b2b182-f26a-4926-be1f-823e14a4ff29.png)

# Most used Maven libraries by version - TOP 100
![2 - Copy](https://user-images.githubusercontent.com/37183688/224573408-2a4ea9b0-987b-4fd2-b49a-95daa6c1a2d9.png)
