---
title: Grundlegendes zu den Unterschieden von Datentypen – Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 906a4abf0768fcad2e5ac31a0ee93345dcc8b30c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027383"
---
# <a name="understanding-data-type-differences"></a>Grundlegendes zu den Unterschieden von Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Es gibt eine Reihe von Unterschieden zwischen den Java-Datentypen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] berücksichtigt diese Unterschiede durch verschiedenartige Konvertierungen.  

## <a name="character-types"></a>Zeichentypen

Die JDBC-Datentypen für Zeichenfolgen sind **CHAR**, **VARCHAR** und **LONGVARCHAR**. Der JDBC-Treiber unterstützt die JDBC 4.0-API. In JDBC 4.0 kann es sich bei den JDBC-Datentypen für Zeichenfolgen auch um **NCHAR**, **NVARCHAR** and **LONGNVARCHAR** handeln. Diese neuen Zeichenfolgentypen verwalten die systemeigenen Java-Zeichentypen im Unicode-Format, sodass keine Konvertierung von ANSI nach Unicode und Unicode nach ANSI mehr erforderlich ist.  
  
| type            | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Feste Länge    | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **char** und **nchar** lassen sich direkt den JDBC-Datentypen **CHAR** bzw. **NCHAR** zuordnen. Diese Typen weisen eine feste Länge auf und werden vom Server mit Leerstellen aufgefüllt, wenn für die Spalte `SET ANSI_PADDING ON` festgelegt wurde. Die Auffüllung mit Leerstellen ist für **nchar** immer aktiviert. Bei **char** fügt der JDBC-Treiber die Leerstellen jedoch nur hinzu, wenn die char-Spalten des Servers nicht aufgefüllt wurden.                                                                                                                                                                                                                                                                                                                                                                                      |
| Variable Länge | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **varchar** und **nvarchar** lassen sich direkt den JDBC-Datentypen **VARCHAR** bzw. **NVARCHAR** zuordnen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen **text** und **ntext** lassen sich den JDBC-Typen **LONGVARCHAR** bzw. **LONGNVARCHAR** zuordnen. Diese Typen sind seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] veraltet, daher sollten Sie stattdessen die Typen mit Unterstützung für umfangreiche Werte wie **varchar(max)** oder **nvarchar(max)** verwenden.<br /><br /> Bei Verwendung der Methoden „update\<Numeric Type>“ und [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) treten bei **text**- und **ntext**-Serverspalten Fehler auf. Allerdings wird die Verwendung der Methode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) mit Angabe eines Zeichenkonvertierungstyps für **text**- und **ntext**-Serverspalten unterstützt. |
  
## <a name="binary-string-types"></a>Binäre Zeichenfolgetypen

Die JDBC-Datentypen für Binärzeichenfolgen sind **BINARY**, **VARBINARY** und **LONGVARBINARY**.  
  
| type            | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Feste Länge    | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **binary** lässt sich direkt dem JDBC-Typ **BINARY** zuordnen. Dieser Typ weist eine feste Länge auf und wird vom Server mit Leerstellen aufgefüllt, wenn für die Spalte SET ANSI_PADDING ON eingestellt wurde. Wenn die Zeichenspalten des Servers nicht mit Leerstellen aufgefüllt sind, fügt der JDBC-Treiber die Leerstellen hinzu.<br /><br /> Bei dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **timestamp** handelt es sich um einen JDBC-**BINARY**-Typ mit einer festen Länge von 8 Bytes. |
| Variable Länge | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **varbinary** lässt sich dem JDBC-Typ **VARBINARY** zuordnen.<br /><br /> Der **udt**-Typ in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt sich in JDBC als **VARBINARY**-Typ zuordnen.                                                                                                                                                                                                                                 |
| Long            | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **image** lässt sich dem JDBC-Typ **LONGVARBINARY** zuordnen. Da dieser Typ ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] veraltet ist, sollten Sie stattdessen einen Typ mit umfangreichen Werten, d.h. **varbinary(max)** , verwenden.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>Exakte numerische Typen

Die exakten numerischen JDBC-Typen sind direkt den entsprechenden SQL Server-Typen zugeordnet.  
  
| type     | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | Der JDBC-Typ **BIT** stellt ein Einzelbit dar, das 0 oder 1 sein kann. Dieser Typ lässt sich einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **bit** zuordnen.                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | Der JDBC-Typ **TINYINT** stellt ein einzelnes Byte dar. Dieser Typ lässt sich einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **tinyint** zuordnen.                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | Der JDBC-Typ **SMALLINT** stellt eine 16-Bit-Ganzzahl mit Vorzeichen dar. Dieser Typ lässt sich einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **smallint** zuordnen.                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | Der JDBC-Typ **INTEGER** stellt eine 32-Bit-Ganzzahl mit Vorzeichen dar. Dieser Typ lässt sich einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **int** zuordnen.                                                                                                                                                                                                                                                                                                                                           |
| bigint   | Der JDBC-Typ **BIGINT** stellt eine 64-Bit-Ganzzahl mit Vorzeichen dar. Dieser Typ lässt sich einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **bigint** zuordnen.                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | Der JDBC-Typ **NUMERIC** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit identischer Genauigkeit enthält. Der Typ **NUMERIC** lässt sich dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **numeric** zuordnen.                                                                                                                                                                                                                                                                   |
| DECIMAL  | Der JDBC-Typ **DECIMAL** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit mindestens der angegebenen Genauigkeit enthält. Der Typ **DECIMAL** lässt sich dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **decimal** zuordnen.<br /><br /> Der JDBC-Typ **DECIMAL** lässt sich außerdem den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen **money** und **smallmoney** zuordnen. Dabei handelt es sich um spezielle Dezimaltypen mit fester Genauigkeit, die in 8 bzw. 4 Bytes gespeichert werden. |
  
## <a name="approximate-numeric-types"></a>Angenäherte numerische Typen

Die angenäherten numerischen JDBC-Typen lauten **REAL**, **DOUBLE** und **FLOAT**.  
  
| type   | Beschreibung                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | Der JDBC-Typ **REAL** weist sieben Stellen für die Genauigkeit auf (einfache Genauigkeit) und lässt sich direkt dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **real** zuordnen.                                                                                                                                     |
| Double | Der JDBC-Typ **DOUBLE** weist 15 Stellen für die Genauigkeit auf (doppelte Genauigkeit) und ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **float** zugeordnet. Der JDBC-Typ **FLOAT** ist ein Synonym von **DOUBLE**. Um Verwechslungen zwischen **FLOAT** und **DOUBLE** zu vermeiden, sollte vorzugsweise **DOUBLE** verwendet werden. |
  
## <a name="datetime-types"></a>Datum-/Zeittypen

Der JDBC-Typ **TIMESTAMP** lässt sich den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen **datetime** und **smalldatetime** zuordnen. Der Typ **datetime** wird in zwei ganzzahligen Werten mit der Länge 4 Byte gespeichert. Der Typ **smalldatetime** enthält die gleichen Informationen (Datum und Uhrzeit), allerdings mit geringerer Genauigkeit in zwei Integer-Werten mit der Länge 2 Byte.  
  
> [!NOTE]  
> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **timestamp** ist ein Binärzeichenfolgentyp mit fester Länge. Er lässt sich keinem der time-Typen in JDBC zuordnen: **DATE**, **TIME** oder **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Benutzerdefinierte Typzuordnung

Die Zuordnungsfunktion für benutzerdefinierte Typen von JDBC, die die SQLData-Schnittstellen für die erweiterten JDBC-Typen (UDTs, Struct usw.) verwendet, ist im JDBC-Treiber nicht implementiert.  
  
## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
