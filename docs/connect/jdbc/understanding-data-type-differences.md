---
title: Grundlegendes zu Datentyp unterschieden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0cec994768fb5c3a49257da0fb310937c79c25b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004164"
---
# <a name="understanding-data-type-differences"></a>Grundlegendes zu den Unterschieden von Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Es gibt eine Reihe von Unterschieden zwischen den Java-Datentypen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] berücksichtigt diese Unterschiede durch verschiedenartige Konvertierungen.  

## <a name="character-types"></a>Zeichentypen

Die JDBC-Zeichen folgen Datentypen lauten **char**, **varchar**und **LONGVARCHAR**. Der JDBC-Treiber unterstützt die JDBC 4.0-API. In JDBC 4,0 können die JDBC-Zeichen folgen Datentypen auch **NCHAR**, **nvarchar**und **LONGNVARCHAR**sein. Diese neuen Zeichenfolgentypen verwalten die systemeigenen Java-Zeichentypen im Unicode-Format, sodass keine Konvertierung von ANSI nach Unicode und Unicode nach ANSI mehr erforderlich ist.  
  
| Typ            | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Feste Länge    | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen **char** und **NCHAR** sind direkt den JDBC-Typen **char** und **NCHAR** zugeordnet. Diese Typen weisen eine feste Länge auf und werden vom Server mit Leerstellen aufgefüllt, wenn für die Spalte `SET ANSI_PADDING ON` festgelegt wurde. Die Auffüllung mit Leerstellen ist für **nchar** immer aktiviert. Bei **char** fügt der JDBC-Treiber die Leerstellen jedoch nur hinzu, wenn die char-Spalten des Servers nicht aufgefüllt wurden.                                                                                                                                                                                                                                                                                                                                                                                      |
| Variable Länge | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Typen **varchar** und **nvarchar** werden direkt den JDBC-Typen **varchar** bzw. **nvarchar** zugeordnet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** -und **ntext** -Typen werden dem JDBC-Typ **LONGVARCHAR** bzw. **LONGNVARCHAR** zugeordnet. Dabei handelt es sich um veraltete Typen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], die mit beginnen. Daher sollten Sie stattdessen die großen Werttypen **varchar (max)** oder **nvarchar (max)** verwenden.<br /><br /> Die Verwendung der\<Methoden zum Aktualisieren numerischer Typen > und [UpdateObject (int, Java. lang. Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) schlägt für **Text** -und **ntext** -Server Spalten fehl. Allerdings wird die Verwendung der Methode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) mit Angabe eines Zeichenkonvertierungstyps für **text**- und **ntext**-Serverspalten unterstützt. |
  
## <a name="binary-string-types"></a>Binäre Zeichenfolgetypen

Die binären JDBC-Zeichen folgen Typen sind **Binary**, **varbinary**und **LONGVARBINARY**.  
  
| Typ            | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Feste Länge    | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **binäre** Typ wird direkt dem JDBC- **Binärtyp** zugeordnet. Dieser Typ weist eine feste Länge auf und wird vom Server mit Leerstellen aufgefüllt, wenn für die Spalte SET ANSI_PADDING ON eingestellt wurde. Wenn die Zeichenspalten des Servers nicht mit Leerstellen aufgefüllt sind, fügt der JDBC-Treiber die Leerstellen hinzu.<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Zeitstempel** -Typ ist ein JDBC- **Binärtyp** mit einer festgelegten Länge von 8 Bytes. |
| Variable Länge | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varbinary** -Typ ist dem JDBC- **varbinary** -Typ zugeordnet.<br /><br /> Der **UDT** -Typ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in wird JDBC als **varbinary** -Typ zugeordnet.                                                                                                                                                                                                                                 |
| Long            | Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bildtyp** wird dem JDBC **LONGVARBINARY** -Typ zugeordnet. Da dieser Typ ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] veraltet ist, sollten Sie stattdessen einen Typ mit umfangreichen Werten, d.h. **varbinary(max)** , verwenden.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>Exakte numerische Typen

Die exakten numerischen JDBC-Typen sind direkt den entsprechenden SQL Server-Typen zugeordnet.  
  
| Typ     | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | Der JDBC-Typ **BIT** stellt ein Einzelbit dar, das 0 oder 1 sein kann. Dies wird einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bittyp** zugeordnet.                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | Der JDBC-Typ **TINYINT** stellt ein einzelnes Byte dar. Dies wird einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint** -Typ zugeordnet.                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | Der JDBC-Typ **SMALLINT** stellt eine 16-Bit-Ganzzahl mit Vorzeichen dar. Dies wird einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **smallint** -Typ zugeordnet.                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | Der JDBC-Typ **INTEGER** stellt eine 32-Bit-Ganzzahl mit Vorzeichen dar. Dies wird einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int** -Typ zugeordnet.                                                                                                                                                                                                                                                                                                                                           |
| bigint   | Der JDBC-Typ **BIGINT** stellt eine 64-Bit-Ganzzahl mit Vorzeichen dar. Dies wird einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bigint** -Typ zugeordnet.                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | Der JDBC-Typ **NUMERIC** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit identischer Genauigkeit enthält. Der **numerische** Typ wird dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **numerischen** Typ zugeordnet.                                                                                                                                                                                                                                                                   |
| DEZIMAL  | Der JDBC-Typ **DECIMAL** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit mindestens der angegebenen Genauigkeit enthält. Der **Decimal** -Typ wird dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Decimal** -Typ zugeordnet.<br /><br /> Der JDBC-Typ **DECIMAL** ist außerdem den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen **money** und **smallmoney** zugeordnet. Dabei handelt es sich um spezielle Dezimaltypen fester Genauigkeit, die in 8 bzw. 4 Byte gespeichert werden. |
  
## <a name="approximate-numeric-types"></a>Angenäherte numerische Typen

Die ungefähren numerischen JDBC-Typen lauten " **Real**", " **Double**" und " **float**".  
  
| Typ   | und Beschreibung                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | Der JDBC-Typ **REAL** weist sieben Ziffern für die Genauigkeit auf (einfache Genauigkeit) und ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **real** zugeordnet.                                                                                                                                     |
| DOUBLE | Der JDBC-Typ **DOUBLE** weist 15 Ziffern für die Genauigkeit auf (doppelte Genauigkeit) und ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **float** zugeordnet. Der JDBC- **float** -Typ ist ein Synonym von **Double**. Da zwischen **float** und **Double**Verwirrung bestehen kann, wird **Double** bevorzugt. |
  
## <a name="datetime-types"></a>Datum-/Zeittypen

Der JDBC- **timestamp** -Typ ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem **DateTime** -Typ und dem **smalldatetime** -Typ zugeordnet. Der Typ **datetime** wird in zwei ganzzahligen Werten mit der Länge 4 Byte gespeichert. Der Typ **smalldatetime** enthält die gleichen Informationen (Datum und Uhrzeit), allerdings mit geringerer Genauigkeit in zwei Integer-Werten mit der Länge 2 Byte.  
  
> [!NOTE]  
> Bei dem Typ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** handelt es sich um einen binären Zeichenfolgentyp mit fester Länge. Er ist keinem der JDBC-Zeit Typen zugeordnet: **Datum**, **Uhrzeit**oder Zeit **Stempel**.  
  
## <a name="custom-type-mapping"></a>Benutzerdefinierte Typzuordnung

Die Zuordnungsfunktion für benutzerdefinierte Typen von JDBC, die die SQLData-Schnittstellen für die erweiterten JDBC-Typen (UDTs, Struct usw.) verwendet, ist im JDBC-Treiber nicht implementiert.  
  
## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
