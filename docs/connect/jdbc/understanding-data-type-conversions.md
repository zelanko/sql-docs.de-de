---
title: Grundlegendes zu Datentypkonvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e46023a364a39950a2fe82fef0cc8357bed6d601
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762408"
---
# <a name="understanding-data-type-conversions"></a>Grundlegendes zu Datentypkonvertierungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Um eine Konvertierung der Datentypen der Programmiersprache Java in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen zu ermöglichen, stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die erforderlichen Datentypkonvertierungen gemäß der JDBC-Spezifikation bereit. Für mehr Flexibilität zu sorgen, werden alle Typen in bzw. aus **Objekt**, **Zeichenfolge**, und **Byte []** -Datentypen.

## <a name="getter-method-conversions"></a>Konvertierungen für Abrufmethoden

Das folgende Diagramm enthält auf Grundlage der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen das Konvertierungsschema des JDBC-Treibers für die get\<Type>()-Methoden der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse und die unterstützten Konvertierungen für die get\<Type>-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse.

![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")

Von den Abrufmethoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)**: Konvertierungen für Fälle, in denen der Abruftyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von getBigDecimal für eine zugrunde liegende dezimale Serverspalte ist beispielsweise keine Konvertierung erforderlich.

- **Converted (y)**: Konvertierungen von numerischen Servertypen zu Java-Typen, bei denen die Konvertierung den Konvertierungsregeln von Java entsprechend erfolgt. Bei diesen Konvertierungen wird die Genauigkeit gekürzt (niemals gerundet), und der Überlauf wird als Modulo des Zieltyps behandelt, der kleiner ist. Zum Beispiel der Aufruf GetInt für eine zugrunde liegende **decimal** Spalte, die von "1,9999" zurück "1", oder, wenn die zugrunde liegende **decimal** Wert ist "3000000000" wird die **Int** Wert führt zu einem Überlauf zu "-1294967296".

- **Data Dependent (z)**: Bei Konvertierungen von zugrunde liegenden Datentypen in numerische Typen müssen die Zeichentypen Werte enthalten, die in den betreffenden Typ konvertiert werden können. Andere Konvertierungen werden nicht ausgeführt. Werte, die für den Abruftyp zu groß sind, sind ungültig. Beim Aufruf von getInt für eine varchar(50)-Spalte, die "53" enthält, wird beispielsweise der Wert als **int** zurückgegeben. Bei einem zugrunde liegenden Wert von "xyz" oder "3000000000" wird ein Fehler ausgegeben.

Wenn GetString aufgerufen wird, auf eine **binäre**, **Varbinary**, **'varbinary(max)'**, oder **Image** Spaltendatentyp als der Wert zurückgegeben wird ein hexadezimaler Zeichenfolgenwert.

## <a name="updater-method-conversions"></a>Konvertierungen für Updatemethoden

Für die Java-Typdaten, die an die \<Type>()-Methoden der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")

Von den Updatemethoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)**: Konvertierungen für Fälle, in denen der Aktualisierungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende dezimale Serverspalte ist beispielsweise keine Konvertierung erforderlich.

- **Converted (y)**: Konvertierungen von numerischen Servertypen zu Java-Typen, bei denen die Konvertierung den Konvertierungsregeln von Java entsprechend erfolgt. Bei diesen Konvertierungen wird die Genauigkeit gekürzt (niemals gerundet), und der Überlauf wird als Modulo des (kleineren) Zieltyps behandelt. Zum Beispiel der Aufruf UpdateDecimal für eine zugrunde liegende **Int** Spalte, die von "1,9999" zurück "1", oder, wenn die zugrunde liegende **decimal** Wert ist "3000000000" wird die **Int**Wert führt zu einem Überlauf zu "-1294967296".

- **Data Dependent (z)**: Bei Konvertierungen von zugrunde liegenden Quelldatentypen zu Zieldatentypen müssen die enthaltenen Werte zu den Zieltypen konvertiert werden können. Andere Konvertierungen werden nicht ausgeführt. Werte, die für den Abruftyp zu groß sind, sind ungültig. Beispielsweise wird das Update bei einem Aufruf von updateString für eine int-Spalte, die "53" enthält, erfolgreich ausgeführt. Bei einem zugrunde liegenden String-Wert von "foo" oder "3000000000" wird ein Fehler ausgelöst.

Wenn UpdateString aufgerufen wird, auf eine **binäre**, **Varbinary**, **'varbinary(max)'**, oder **Image** Spaltendatentyp den Zeichenfolgenwert verarbeitet als hexadezimale Zeichenfolge zurück.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim UpdateBytes, UpdateBinaryStream oder UpdateBlob-Methoden aufrufen, sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Zum Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="setter-method-conversions"></a>Konvertierungen für Festlegungsmethoden

Für die Java-Typdaten, die an die \<Type>()-Methoden der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse und der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")

Der Server versucht alle Konvertierungen und gibt bei Fehlern eine Fehlermeldung zurück.

Im Fall von der **Zeichenfolge** -Datentyp, wenn der Wert die Länge von überschreitet **VARCHAR**, entspricht dem **LONGVARCHAR**. Auf ähnliche Weise **NVARCHAR** ordnet **LONGNVARCHAR** überschreitet der Wert die Länge von **NVARCHAR**. Das gleiche gilt für **byte[]**. Werte mit mehr als **VARBINARY** werden **LONGVARBINARY**.

Von den Festlegungsmethoden des JDBC-Treibers werden zwei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)**: Konvertierungen für numerische Fälle, in denen der Festlegungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende **dezimale** Serverspalte ist beispielsweise keine Konvertierung erforderlich. Bei der Umwandlung von numerischen Typen in Zeichentypen wird der **numerische** Java-Datentyp in eine **Zeichenfolge** konvertiert. Beim Aufruf von setDouble für eine varchar(50)-Spalte mit dem Wert "53" wird beispielsweise in der betreffenden Zielspalte der Zeichenwert "53" erzeugt.

- **Konvertierte (y)**: Konvertierungen von einem Java **numerischen** Typ in einen zugrunde liegenden **numerischen** Typ, der kleiner ist. Diese Konvertierung ist regulär und erfolgt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungskonventionen entsprechend. Die Genauigkeit wird immer gekürzt (niemals gerundet). Bei einem Überlauf wird der Fehler ausgegeben, dass die Konvertierung nicht unterstützt wird. Beispielsweise führt updateDecimal mit einem Wert von "1,9999" für eine zugrunde liegende integer-Spalte zu einer "1" in der Zielspalte. Bei Übergabe von "3000000000" löst der Treiber jedoch einen Fehler aus.

- **Daten abhängige (Z)**: Konvertierungen von einem Java **Zeichenfolge** Typ auf den zugrunde liegenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp hängt von folgenden Bedingungen: der Treiber sendet die **Zeichenfolge** Wert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt Konvertierungen, bei Bedarf. Wenn sendStringParametersAsUnicode auf TRUE festgelegt ist und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Konvertierung von **nvarchar** in **image** zu und löst eine SQLServerException-Ausnahme aus. Wenn sendStringParametersAsUnicode auf FALSE festgelegt und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Konvertierung von **varchar** in **image** zu, und es wird keine Ausnahme ausgelöst.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt die Konvertierungen aus und übergibt Fehler bei Problemen wieder an den JDBC-Treiber.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim UpdateBytes, UpdateBinaryStream oder UpdateBlob-Methoden aufrufen, sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Zum Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="conversions-on-setobject"></a>Konvertierungen für setObject

> [!NOTE]  
> Microsoft JDBC-Treiber 4.2 (und höher) für SQL Server JDBC 4.1 und 4.2 unterstützt. Weitere Informationen zu den Versionen 4.1 und 4.2 datentypzuordnungen und-Konvertierungen finden Sie unter [JDBC 4.1-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) und [JDBC 4.2-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md), zusätzlich zu den folgenden Informationen.

Für die Java-Typdaten, die an die setObject(\<Type>)-Methoden der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")

Die setObject-Methode ohne Angabe eines Zieltyps verwendet die Standardzuordnung. Im Fall von der **Zeichenfolge** -Datentyp, wenn der Wert die Länge von überschreitet **VARCHAR**, entspricht dem **LONGVARCHAR**. Auf ähnliche Weise **NVARCHAR** ordnet **LONGNVARCHAR** überschreitet der Wert die Länge von **NVARCHAR**. Das gleiche gilt für **byte[]**. Werte mit mehr als **VARBINARY** werden **LONGVARBINARY**.

Von den setObject-Methoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)**: Konvertierungen für numerische Fälle, in denen der Festlegungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende **dezimale** Serverspalte ist beispielsweise keine Konvertierung erforderlich. Bei der Umwandlung von numerischen Typen in Zeichentypen wird der **numerische** Java-Datentyp in eine **Zeichenfolge** konvertiert. Beim Aufruf von setDouble für eine varchar(50)-Spalte mit dem Wert "53" wird beispielsweise in der betreffenden Zielspalte der Zeichenwert "53" erzeugt.

- **Konvertierte (y)**: Konvertierungen von einem Java **numerischen** Typ in einen zugrunde liegenden **numerischen** Typ, der kleiner ist. Diese Konvertierung ist regulär und erfolgt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungskonventionen entsprechend. Die Genauigkeit wird immer gekürzt (niemals gerundet). Bei einem Überlauf wird der Fehler ausgegeben, dass die Konvertierung nicht unterstützt wird. Beispielsweise führt updateDecimal mit einem Wert von "1,9999" für eine zugrunde liegende integer-Spalte zu einer "1" in der Zielspalte. Bei Übergabe von "3000000000" löst der Treiber jedoch einen Fehler aus.

- **Daten abhängige (Z)**: Konvertierungen von einem Java **Zeichenfolge** Typ auf den zugrunde liegenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp hängt von folgenden Bedingungen: der Treiber sendet die **Zeichenfolge** Wert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt Konvertierungen, bei Bedarf. Wenn die sendStringParametersAsUnicode-Verbindungseigenschaft auf TRUE festgelegt ist und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Konvertierung von **nvarchar** in **image** zu und löst eine SQLServerException-Ausnahme aus. Wenn sendStringParametersAsUnicode auf FALSE festgelegt und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Konvertierung von **varchar** in **image** zu, und es wird keine Ausnahme ausgelöst.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt den Großteil der Festlegungskonvertierungen aus und gibt bei Problemen Fehler an den JDBC-Treiber zurück. Clientseitige Konvertierungen sind die Ausnahme und erfolgt nur im Fall von **Datum**, **Zeit**, **Zeitstempel**, **booleschen**, und  **Zeichenfolge** Werte.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim Aufrufen der Methoden setObject(byte[], SQLXML), setObject(inputStream, SQLXML) oder setObject(Blob, SQLXML) sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Zum Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
