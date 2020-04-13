---
title: Verwenden der Option BINARY BASE64 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: RothJa
ms.author: jroth
ms.openlocfilehash: 42b2e41bedbce625d38b9d73a06b62817419c92c
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665243"
---
# <a name="use-the-binary-base64-option"></a>Verwenden der Option BINARY BASE64

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Wenn die Option BINARY BASE64 in der Abfrage angegeben ist, werden die Binärdaten im Base64-codierten Format zurückgegeben.

Wenn die Option BINARY BASE64 nicht in der Abfrage angegeben ist, unterstützt standardmäßig der AUTO-Modus die URL-Codierung von Binärdaten. Es wird ein Verweis auf eine relative URL-Adresse des virtuellen Stamms der Datenbank zurückgegeben. Dieser Verweis bezieht sich auf die Datenbank in der die Abfrage ausgeführt wurde. Der zurückgegebene Verweis kann in nachfolgenden Vorgängen für den Zugriff auf die eigentlichen Binärdaten verwendet werden. Dieser Zugriff wird durch Verwenden der SQLXML ISAPI-dbobject-Abfrage erreicht. Die Abfrage muss genügend Informationen zum Identifizieren des Images angeben. Zu diesen Informationen können die Spalten des Primärschlüssels zählen.

## <a name="column-alias"></a>Spaltenalias

Verwenden Sie keinen Alias für eine Binärspalte, wenn Sie im FOR XML AUTO-Modus eine Ansicht abfragen. Wenn Sie einen Alias verwenden, wird der Alias in der URL-Codierung der Binärdaten zurückgegeben. In nachfolgenden Vorgängen ist der Alias bedeutungslos. Der bedeutungslose Alias und die URL-Codierung können nicht zum Abrufen des Images verwendet werden.

### <a name="cast-to-a-blob"></a>Umwandlung in ein BLOB

In einer SELECT-Abfrage wird jede beliebige Spalte durch Umwandlung in ein BLOB (Binary Large Object) zu einer temporären Entität. Als temporäre Entität verliert das BLOB seinen zugeordneten Tabellennamen und Spaltennamen. Abfragen im AUTO-Modus geben bei dieser Umwandlung einen Fehler aus, da das System den Wert nicht in der XML-Hierarchie einordnen kann.

Betrachten Sie dazu beispielsweise die folgende Tabelle mit ihrer einen Zeile.

```sql
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)
INSERT INTO MyTable VALUES (1, 0x7);
```

Die folgende Abfrage führt aufgrund der Umwandlung in ein BLOB (Binary Large Object) zu einem Fehler:

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO;
```

Die Lösung besteht im Hinzufügen der Option BINARY BASE64 zur FOR XML-Klausel. Wenn Sie die Umwandlung entfernen, liefert die Abfrage gute Ergebnisse.

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO, BINARY BASE64;
```

Erwarten Sie Folgendes gutes Ergebnis:

```console
<MyTable Col1="1" Col2="Bw==" />
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden des AUTO-Modus mit FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)
