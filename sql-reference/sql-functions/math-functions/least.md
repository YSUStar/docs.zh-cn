# least

## ## 功能

返回多个输入参数中的最小值。

通常情况下，返回值的数据类型与输入值相同。

该函数在对比时遵循的原则同 [greatest](./greatest.md) 。

## 语法

```Haskell
LEAST(expr1,...);
```

## 参数

`expr1`: 支持的数据类型为 SMALLINT、TINYINT、INT、BIGINT、LARGEINT、FLOAT、DOUBLE、DECIMALV2、DECIMAL32、DECIMAL64、DECIMAL128、DATETIME、VARCHAR

## 示例

示例一：输入值为单值。

```Plain
select least(3);
+----------+
| least(3) |
+----------+
|        3 |
+----------+
1 row in set (0.00 sec)
```

示例二：返回一组数值中的最小值。

```Plain
select least(3,4,5,5,6);
+----------------------+
| least(3, 4, 5, 5, 6) |
+----------------------+
|                    3 |
+----------------------+
1 row in set (0.01 sec)
```

示例三：输入值中包含 DOUBLE 类型值，所有值按照 DOUBLE 类型进行比较，并返回 DOUBLE 类型的值。

```Plain
select least(4,4.5,5.5);
+--------------------+
| least(4, 4.5, 5.5) |
+--------------------+
|                4.0 |
+--------------------+
```

示例四：输入值包含数值和字符串类型且字符串可以转换为数值，按照数值进行比较。

```Plain
select least(7,'5');
+---------------+
| least(7, '5') |
+---------------+
| 5             |
+---------------+
1 row in set (0.01 sec)
```

示例五：输入值包含数值和字符串类型，且字符串不可以转换为数值，按照字符串进行比较。字符串 `'1'` 小于`'at'`。

```Plain
select least(1,'at');
+----------------+
| least(1, 'at') |
+----------------+
| 1              |
+----------------+
```

示例六：输入值全部为字符型，最小值为字母表第一位 `A`。

```Plain
mysql> select least('A','B','Z');
+----------------------+
| least('A', 'B', 'Z') |
+----------------------+
| A                    |
+----------------------+
1 row in set (0.00 sec)
```