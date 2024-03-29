※PDFファイルからコピーしているので改行やスペースがおかしいことがあるかもしれません

Q3.1
```
CREATE TABLE ワイン(ワインID bigint PRIMARY KEY, 名前 varchar, 産地 varchar, 品種 varchar, 色 varchar, タイプ varchar, ビンテージ bigint, 価格 bigint);
```
  
Q3.2
```
INSERT INTO ワイン(ワインID, 名前, 産地, 品種, 色, タイプ, ビンテージ, 価格) VALUES
(1, 'シャプリ', 'ブルゴーニュ', 'シャルドネ', '白', 'スティール', 2001, 2400),
(2, 'ジュヴレシャンベルタン', 'ブルゴーニュ', 'ピノノワール', '赤', 'スティール', 1998, 3000),
(3, 'サンテミリオン', 'ボルドー', 'メルロー', '赤', 'スティール', 1997, 5800),
(4, 'オーメドック', 'ボルドー', 'カベルネ・ソーヴィニヨン','赤', 'スティール', 1997, 2200),
(5, 'サンセール', 'ロワール', 'ソーヴィニヨンブラン', '白', 'スティール' , 2001, 2800),
(6, 'シャンパン', 'シャンパーニュ', 'シャルドネ', '白', 'スパーククリング', 1999, 4000);
```

Q3.3  
```
CREATE VIEW デイリーワイン(名前, 産地, ビンテージ, 価格) AS SELECT 名前,産地,ビンテージ,価格 FROM ワイン WHERE 価格 < 3000;
```

Q3.4
```
CREATE VIEW 白ワイン(名前, 産地, ビンテージ, 価格) AS SELECT 名前, 産地, ビンテージ,価格 FROM ワイン WHERE 色 = '白';
```

Q3.5
```
SELECT * FROM デイリーワイン EXCEPT (SELECT * FROM 白ワイン);
```

Q3.6  
```
SELECT ワインID FROM ワイン WHERE 名前 LIKE 'シャ__';
```

Q3.7  
```
SELECT *, CASE
WHEN 価格 < 3000 THEN 'デイリー'
WHEN 価格 >= 3000 AND 価格 < 4000 THEN '中級'
WHEN 価格 >= 5000 THEN '高級'
ELSE '不明'
END AS カテゴリ
FROM ワイン;
```

Q3.8
```
SELECT 色, タイプ, MAX(価格) AS 最高価格 FROM ワイン GROUP BY 色, タイプ ORDER BY 最高価格 DESC;
```

演習２（準備）  
```
CREATE TABLE ワイン(ワインID bigint, 名前 varchar, 産地 varchar, 品種 varchar, 色
varchar, タイプ varchar, ビンテージ bigint, 価格 bigint);
INSERT INTO ワイン(ワインID, 名前, 産地, 品種, 色, タイプ, ビンテージ, 価格) VALUES
(1, 'シャブリ','ブルゴーニュ', 'シャルドネ', '白', 'スティール', 2001, 2400),
(2, 'ジュヴレシャンベルタン', 'ブルゴーニュ', 'ピノノワール', '赤', 'スティール', 1998, 3000),
(3, 'サンテミリオン', 'ボルドー', 'メルロー', '赤', 'スティール', 1997, 5800),
(4, 'オーメドック', 'ボルドー', 'カベルネ・ソーヴィニヨン', '赤', 'スティール', 1997, 2200),
(5, 'サンセール', 'ロワール', 'ソーヴィニヨンブラン', '白', 'スティール', 2001, 2800),
(6, 'シャンパン', 'シャンパーニュ', 'シャルドネ', '白', 'スパークリング', 1999, 4000);
```
  
```
CREATE TABLE ワインセット(セットID bigint PRIMARY KEY, 名前 varchar, 本数 bigint,
価格 bigint);
INSERT INTO ワインセット(セットID, 名前, 本数, 価格) VALUES (1, 'ブルゴーニュセット', 2,5400), (2, 'ボルドーセット', 2, 8000), (3, '白ワインセット', 2, 5200), (4, '赤ワインセット', 3,11000);
```
  
```
CREATE TABLE セット内容(セットID bigint, ワインID bigint, PRIMARY KEY (セットID,ワインID));
INSERT INTO セット内容( セットID, ワインID )VALUES (1,1), (1,2),(2,3),(2,4),(3,1),(3,5),(4,2),(4,3),(4,4);
```
  
```
CREATE TABLE 生産地(産地 varchar PRIMARY KEY, 国名 varchar);
INSERT INTO 生産地(産地, 国名) VALUES ('シャンパーニュ', 'フランス'), ('ソーテルヌ', 'フランス'), ('トカイ', 'ハンガリー'), ('ブルゴーニュ', 'フランス'), ('ボルドー', 'フランス'), ('ラインガウ', 'ドイツ'), ('ロワール', 'フランス');
```
  
```
CREATE TABLE AOC品質ワイン(ワインID bigint, 名前 varchar, 産地 varchar, 品種 varchar,色 varchar, タイプ varchar, ビンテージ bigint, 価格 bigint);
INSERT INTO AOC品質ワイン(ワインID, 名前, 産地, 品種, 色, タイプ, ビンテージ, 価格)
VALUES (2, 'ジュヴレシャンベルタン', 'ブルゴーニュ', 'ピノノワール', '赤', 'スティール', 1998,3000),
(3, 'サンテミリオン', 'ボルドー', 'メルロー', '赤', 'スティール', 1997, 5800),
(7, 'シャトーマルゴー', 'ボルドー', 'カベルネ・ソーヴィニヨン', '赤', 'スティール', 2003, 100000 ),
(8, 'シャトーラトゥール', 'ボルドー', 'カベルネ・ソーヴィニヨン', '赤', 'スティール', 2005, 80000 );
```

Q4.1  
```
SELECT * FROM ワイン WHERE ワインID NOT IN (SELECT ワインID FROM AOC品質ワイン);
```

Q4.2
```
(1)SELECT DISTINCT SC.セットID FROM セット内容 AS SC
WHERE 1 = (SELECT COUNT(DISTINCT 色) FROM ワイン NATURAL JOIN セット内容
WHERE セットID=SC.セットID);
```
```
(2)SELECT DISTINCT SC.セットID FROM セット内容 AS SC
GROUP BY SC.セットID
HAVING 1 = (SELECT COUNT(DISTINCT 色) FROM ワイン NATURAL JOIN セット内容
WHERE セットID=SC.セットID);
```
Q4.3  
```
SELECT WS.名前 FROM ワインセット AS WS
GROUP BY WS.セットID
HAVING NOT EXISTS(
SELECT * FROM ワイン
NATURAL JOIN 生産地
NATURAL JOIN セット内容
INNER JOIN ワインセット USING (セットID)
WHERE NOT 国名='フランス' AND セットID = WS.セットID);
```
Q4.4
```
SELECT * FROM ワイン AS W FULL OUTER JOIN AOC 品質ワイン AS AW USING (ワインID) WHERE W.ビンテージ >= 1998 OR AW.ビンテージ >= 1998;
```
Q4.5
```
UPDATE AOC 品質ワイン SET 価格 = 価格 * 1.3 WHERE ビンテージ = 2003;
```
