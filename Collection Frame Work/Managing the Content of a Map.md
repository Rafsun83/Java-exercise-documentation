# Overview
> You can simply add a key/value pair in a map with put(key, value). If the key is not already present in the map, then the key/value pair is simply added to the map. If it is, then the existing value is replaced with the new one.

## 1. Adding a Key Value Pair to a `Map`
> Java SE 8 introduces the putIfAbsent() method. This method can also add a key/value pair to the map, only if the key is not already present and not associated to a null value. This may seem a bit confusing at first, but putIfAbsent() will replace a null value with the new value provided.

> **_You may fix this map with the following code, which replaces the faulty null values with a default value, -1, that will not generate any NullPointerException anymore._**
```java
Map<String, Integer> map = new HashMap<>();

map.put("one", 1);
map.put("two", null);
map.put("three", 3);
map.put("four", null);
map.put("five", 5);

//Print map
for (int value : map.values()) {
    System.out.println("value = " + value);
}

//Replaced null value by putIfAbsent
for (String key : map.keySet()) {
    map.putIfAbsent(key, -1);
}
//Output        
value = -1
value = 1
value = -1
value = 3
value = 5
```

## 2. Getting a Value From a Key
> Java SE 8 introduced the getOrDefault() method that takes a key and a default value which is returned if the key is not in the map.

```java
Map<Integer, String> map = new HashMap<>();

map.put(1, "one");
map.put(2, "two");
map.put(3, "three");

List<String> values = new ArrayList<>();
for (int key = 0; key < 5; key++) {
    values.add(map.getOrDefault(key,"UNDEFINED"));
}

System.out.println("values = " + values);

//Output
values = [UNDEFINED, one, two, three, UNDEFINED]
```
