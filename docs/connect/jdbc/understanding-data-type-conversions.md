---
title: Grundlegendes zu Datentypkonvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ed91f1b38f68715cd174a96cb2f0364fc060482
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027485"
---
# <a name="understanding-data-type-conversions"></a>Grundlegendes zu Datentypkonvertierungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Um eine Konvertierung der Datentypen der Programmiersprache Java in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen zu ermöglichen, stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die erforderlichen Datentypkonvertierungen gemäß der JDBC-Spezifikation bereit. Alle Typen können in die und aus den Datentypen **Objekt**, **Zeichenfolge** und **Byte[]** konvertiert werden, um die Flexibilität zu erweitern.

## <a name="getter-method-conversions"></a>Konvertierungen für Abrufmethoden

Das folgende Diagramm enthält auf Grundlage der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen das Konvertierungsschema des JDBC-Treibers für die get\<Type>()-Methoden der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse und die unterstützten Konvertierungen für die get\<Type>-Methoden der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse.

![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")

Von den Abrufmethoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)** : Konvertierungen für Fälle, in denen der Abruftyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von getBigDecimal für eine zugrunde liegende dezimale Serverspalte ist beispielsweise keine Konvertierung erforderlich.

- **Converted (y)** : Konvertierungen von numerischen Servertypen zu Java-Typen, bei denen die Konvertierung entsprechend den Konvertierungsregeln von Java erfolgt. Bei diesen Konvertierungen wird die Genauigkeit gekürzt (niemals gerundet), und der Überlauf wird als Modulo des Zieltyps behandelt, der kleiner ist. Beim Aufruf von getInt für eine zugrunde liegende **Dezimalspalte** mit dem Wert „1,9999“ wird beispielsweise der Wert „1“ zurückgegeben. Beim zugrunde liegenden **Dezimalwert** „3000000000“ beträgt der Überlauf des **int**-Werts dann „-1294967296“.

- **Data Dependent (z)** : Bei Konvertierungen von zugrunde liegenden Datentypen in numerische Typen müssen die Zeichentypen Werte enthalten, die in den betreffenden Typ konvertiert werden können. Andere Konvertierungen werden nicht ausgeführt. Werte, die für den Abruftyp zu groß sind, sind ungültig. Beim Aufruf von getInt für eine varchar(50)-Spalte, die "53" enthält, wird beispielsweise der Wert als **int** zurückgegeben. Bei einem zugrunde liegenden Wert von "xyz" oder "3000000000" wird ein Fehler ausgegeben.

Wenn getString für einen **binären**, **varbinary**-, **varbinary(max)** - oder **image**-Spaltendatentyp aufgerufen wird, wird der Wert als hexadezimaler Zeichenfolgenwert zurückgegeben.

## <a name="updater-method-conversions"></a>Konvertierungen für Updatemethoden

Für die Java-Typdaten, die an die \<Type>()-Methoden der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")

Von den Updatemethoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)** : Konvertierungen für Fälle, in denen der Aktualisierungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende dezimale Serverspalte ist beispielsweise keine Konvertierung erforderlich.

- **Converted (y)** : Konvertierungen von numerischen Servertypen zu Java-Typen, bei denen die Konvertierung entsprechend den Konvertierungsregeln von Java erfolgt. Bei diesen Konvertierungen wird die Genauigkeit gekürzt (niemals gerundet), und der Überlauf wird als Modulo des (kleineren) Zieltyps behandelt. Beim Aufruf von updateDecimal für eine zugrunde liegende **int**-Spalte mit dem Wert „1,9999“ wird beispielsweise der Wert „1“ zurückgegeben. Beim zugrunde liegenden **Dezimalwert** „3000000000“ beträgt der Überlauf des **int**-Werts dann „-1294967296“.

- **Data Dependent (z)** : Bei Konvertierungen von zugrunde liegenden Quelldatentypen in Zieldatentypen müssen die enthaltenen Werte in die Zieltypen konvertiert werden können. Andere Konvertierungen werden nicht ausgeführt. Werte, die für den Abruftyp zu groß sind, sind ungültig. Beispielsweise wird das Update bei einem Aufruf von updateString für eine int-Spalte, die "53" enthält, erfolgreich ausgeführt. Bei einem zugrunde liegenden String-Wert von "foo" oder "3000000000" wird ein Fehler ausgelöst.

Wenn updateString für einen **binären**, **varbinary**-, **varbinary(max)** - oder **image**-Spaltendatentyp aufgerufen wird, wird der Zeichenfolgenwert als hexadezimaler Zeichenfolgenwert zurückgegeben.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim Aufrufen der Methoden updateBytes, updateBinaryStream oder updateBlob sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="setter-method-conversions"></a>Konvertierungen für Festlegungsmethoden

Für die Java-Typdaten, die an die \<Type>()-Methoden der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse und der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")

Der Server versucht alle Konvertierungen und gibt bei Fehlern eine Fehlermeldung zurück.

Wenn der Wert eines **String**-Datentyps die Länge von **VARCHAR** überschreitet, wird er **LONGVARCHAR** zugeordnet. Ebenso wird **NVARCHAR** **LONGNVARCHAR** zugeordnet, wenn der Wert die unterstützte Länge von **NVARCHAR** überschreitet. Das gleiche gilt für **byte[]** . Werte, die länger sind als **VARBINARY**, werden zu **LONGVARBINARY**.

Von den Festlegungsmethoden des JDBC-Treibers werden zwei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)** : Konvertierungen für numerische Fälle, in denen der Festlegungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende **dezimale** Serverspalte ist beispielsweise keine Konvertierung erforderlich. Bei der Umwandlung von numerischen Typen in Zeichentypen wird der **numerische** Java-Datentyp in eine **Zeichenfolge** konvertiert. Beim Aufruf von setDouble für eine varchar(50)-Spalte mit dem Wert "53" wird beispielsweise in der betreffenden Zielspalte der Zeichenwert "53" erzeugt.

- **Converted (y)** : Konvertierungen eines **numerischen** Java-Typs in einen zugrunde liegenden **numerischen** Servertyp, der kleiner ist. Diese Konvertierung ist regulär und erfolgt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungskonventionen entsprechend. Die Genauigkeit wird immer gekürzt (niemals gerundet). Bei einem Überlauf wird der Fehler ausgegeben, dass die Konvertierung nicht unterstützt wird. Beispielsweise führt updateDecimal mit einem Wert von "1,9999" für eine zugrunde liegende integer-Spalte zu einer "1" in der Zielspalte. Bei Übergabe von "3000000000" löst der Treiber jedoch einen Fehler aus.

- **Data Dependent (z)** : Konvertierungen von einem **Zeichenfolgen**-Java-Typ in den zugrunde liegenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp hängen von den folgenden Bedingungen ab: Der Treiber sendet den **Zeichenfolgen**-Wert an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt ggf. notwendige Konvertierungen durch. Wenn sendStringParametersAsUnicode auf TRUE festgelegt ist und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Konvertierung von **nvarchar** in **image** zu und löst eine SQLServerException-Ausnahme aus. Wenn sendStringParametersAsUnicode auf FALSE festgelegt und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Konvertierung von **varchar** in **image** zu, und es wird keine Ausnahme ausgelöst.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt die Konvertierungen aus und übergibt Fehler bei Problemen wieder an den JDBC-Treiber.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim Aufrufen der Methoden updateBytes, updateBinaryStream oder updateBlob sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="conversions-on-setobject"></a>Konvertierungen für setObject

> [!NOTE]  
> Der Microsoft JDBC-Treiber 4.2 (und höher) für SQL Server unterstützt JDBC 4.1 und 4.2. Weitere Informationen zu den Datentypzuordnungen und -konvertierungen von 4.1 und 4.2 finden Sie zusätzlich zu den unten aufgeführten Informationen unter [JDBC 4.1-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) und [JDBC 4.2-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

Für die Java-Typdaten, die an die setObject(\<Type>)-Methoden der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse übergeben werden, gelten die folgenden Konvertierungen.

![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")

Die setObject-Methode ohne Angabe eines Zieltyps verwendet die Standardzuordnung. Wenn der Wert eines **String**-Datentyps die Länge von **VARCHAR** überschreitet, wird er **LONGVARCHAR** zugeordnet. Ebenso wird **NVARCHAR** **LONGNVARCHAR** zugeordnet, wenn der Wert die unterstützte Länge von **NVARCHAR** überschreitet. Das gleiche gilt für **byte[]** . Werte, die länger sind als **VARBINARY**, werden zu **LONGVARBINARY**.

Von den setObject-Methoden des JDBC-Treibers werden drei Konvertierungskategorien unterstützt:

- **Non-Lossy (x)** : Konvertierungen für numerische Fälle, in denen der Festlegungstyp maximal dem zugrunde liegenden Servertyp entspricht. Beim Aufruf von updateBigDecimal für eine zugrunde liegende **dezimale** Serverspalte ist beispielsweise keine Konvertierung erforderlich. Bei der Umwandlung von numerischen Typen in Zeichentypen wird der **numerische** Java-Datentyp in eine **Zeichenfolge** konvertiert. Beim Aufruf von setDouble für eine varchar(50)-Spalte mit dem Wert "53" wird beispielsweise in der betreffenden Zielspalte der Zeichenwert "53" erzeugt.

- **Converted (y)** : Konvertierungen eines **numerischen** Java-Typs in einen zugrunde liegenden **numerischen** Servertyp, der kleiner ist. Diese Konvertierung ist regulär und erfolgt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungskonventionen entsprechend. Die Genauigkeit wird immer gekürzt (niemals gerundet). Bei einem Überlauf wird der Fehler ausgegeben, dass die Konvertierung nicht unterstützt wird. Beispielsweise führt updateDecimal mit einem Wert von "1,9999" für eine zugrunde liegende integer-Spalte zu einer "1" in der Zielspalte. Bei Übergabe von "3000000000" löst der Treiber jedoch einen Fehler aus.

- **Data Dependent (z)** : Konvertierungen von einem **Zeichenfolgen**-Java-Typ in den zugrunde liegenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp hängen von den folgenden Bedingungen ab: Der Treiber sendet den **Zeichenfolgen**-Wert an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt ggf. notwendige Konvertierungen durch. Wenn die sendStringParametersAsUnicode-Verbindungseigenschaft auf TRUE festgelegt ist und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Konvertierung von **nvarchar** in **image** zu und löst eine SQLServerException-Ausnahme aus. Wenn sendStringParametersAsUnicode auf FALSE festgelegt und der zugrunde liegende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **image** ist, lässt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Konvertierung von **varchar** in **image** zu, und es wird keine Ausnahme ausgelöst.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt den Großteil der Festlegungskonvertierungen aus und gibt bei Problemen Fehler an den JDBC-Treiber zurück. Clientseitige Konvertierungen sind die Ausnahme und werden nur bei **date**-, **time**-, **timestamp**-, **Boolean**- und **Zeichenfolgen**-Werten ausgeführt.

Wenn der Datentyp der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spalte **XML** ist, muss der Datenwert ein gültiger **XML**-Wert sein. Beim Aufrufen der Methoden setObject(byte[], SQLXML), setObject(inputStream, SQLXML) oder setObject(Blob, SQLXML) sollte der Datenwert die hexadezimale Zeichenfolgendarstellung der XML-Zeichen sein. Beispiel:

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Beachten Sie, dass eine Bytereihenfolge-Marke (BOM) erforderlich ist, wenn die XML-Zeichen in einer bestimmten Zeichencodierung vorliegen.

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
