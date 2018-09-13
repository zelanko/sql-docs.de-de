---
title: Kenntnisse der Unterschiede von Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 105c7d5baa3c2ad7064bf95787975eca2b8c4863
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784431"
---
# <a name="understanding-data-type-differences"></a>Grundlegendes zu den Unterschieden von Datentypen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Es gibt eine Reihe von Unterschieden zwischen den Java-Datentypen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] berücksichtigt diese Unterschiede durch verschiedenartige Konvertierungen.  

## <a name="character-types"></a>Zeichentypen

Der JDBC-Zeichenfolgentypen werden **CHAR**, **VARCHAR**, und **LONGVARCHAR**. Der JDBC-Treiber unterstützt die JDBC 4.0-API. In JDBC 4.0 sind die JDBC-Zeichenfolgentypen können auch sein **NCHAR**, **NVARCHAR**, und **LONGNVARCHAR**. Diese neuen Zeichenfolgentypen verwalten die systemeigenen Java-Zeichentypen im Unicode-Format, sodass keine Konvertierung von ANSI nach Unicode und Unicode nach ANSI mehr erforderlich ist.  
  
| Typ            | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Feste Länge    | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Char** und **Nchar** Datentypen zugeordnet werden, direkt mit dem JDBC **CHAR** und **NCHAR** Typen. Diese Typen weisen eine feste Länge auf und werden vom Server mit Leerstellen aufgefüllt, wenn für die Spalte `SET ANSI_PADDING ON` festgelegt wurde. Die Auffüllung mit Leerstellen ist für **nchar** immer aktiviert. Bei **char** fügt der JDBC-Treiber die Leerstellen jedoch nur hinzu, wenn die char-Spalten des Servers nicht aufgefüllt wurden.                                                                                                                                                                                                                                                                                                                                                                                      |
| Variable Länge | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Varchar** und **Nvarchar** Typen direkt direkt den JDBC **VARCHAR** und **NVARCHAR** bzw. Typen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** und **Ntext** Typen direkt den JDBC **LONGVARCHAR** und **LONGNVARCHAR** vom Typ. Diese Typen sind veraltet ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], daher sollten Sie die Typen mit umfangreichen Werten verwenden **varchar(max)** oder **nvarchar(max)** stattdessen.<br /><br /> Verwenden das Update\<numerischen Typ > und [UpdateObject (Int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) -Methode treten für **Text** und **Ntext** Server-Spalten. Allerdings wird die Verwendung der Methode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) mit Angabe eines Zeichenkonvertierungstyps für **text**- und **ntext**-Serverspalten unterstützt. |
  
## <a name="binary-string-types"></a>Binäre Zeichenfolgetypen

Werden die binären JDBC-Zeichenfolgentypen **BINÄRE**, **VARBINARY**, und **LONGVARBINARY**.  
  
| Typ            | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Feste Länge    | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **binäre** geben wird direkt dem JDBC **BINÄRE** Typ. Dieser Typ weist eine feste Länge auf und wird vom Server mit Leerstellen aufgefüllt, wenn für die Spalte SET ANSI_PADDING ON eingestellt wurde. Wenn die Zeichenspalten des Servers nicht mit Leerstellen aufgefüllt sind, fügt der JDBC-Treiber die Leerstellen hinzu.<br /><br /> Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Zeitstempel** Typ ist ein JDBC **BINÄRE** Typ mit einer festen Länge von 8 Bytes. |
| Variable Länge | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Varbinary** wird automatisch in der JDBC **VARBINARY** Typ.<br /><br /> Die **Udt** Geben Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC ordnet eine **VARBINARY** Typ.                                                                                                                                                                                                                                 |
| Long            | Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Image** wird automatisch in der JDBC **LONGVARBINARY** Typ. Da dieser Typ ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] veraltet ist, sollten Sie stattdessen einen Typ mit umfangreichen Werten, d.h. **varbinary(max)**, verwenden.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>Exakte numerische Typen

Die exakten numerischen JDBC-Typen sind direkt den entsprechenden SQL Server-Typen zugeordnet.  
  
| Typ     | und Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | Der JDBC-Typ **BIT** stellt ein Einzelbit dar, das 0 oder 1 sein kann. Dies ordnet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bit** Typ.                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | Der JDBC-Typ **TINYINT** stellt ein einzelnes Byte dar. Dies ordnet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tinyint** Typ.                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | Der JDBC-Typ **SMALLINT** stellt eine 16-Bit-Ganzzahl mit Vorzeichen dar. Dies ordnet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Smallint** Typ.                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | Der JDBC-Typ **INTEGER** stellt eine 32-Bit-Ganzzahl mit Vorzeichen dar. Dies ordnet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Int** Typ.                                                                                                                                                                                                                                                                                                                                           |
| bigint   | Der JDBC-Typ **BIGINT** stellt eine 64-Bit-Ganzzahl mit Vorzeichen dar. Dies ordnet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bigint** Typ.                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | Der JDBC-Typ **NUMERIC** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit identischer Genauigkeit enthält. Die **numerischen** Typ zugeordnet werden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **numerischen** Typ.                                                                                                                                                                                                                                                                   |
| DECIMAL  | Der JDBC-Typ **DECIMAL** stellt einen Dezimalwert fester Genauigkeit dar, der Werte mit mindestens der angegebenen Genauigkeit enthält. Die **DECIMAL** Typ zugeordnet werden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **decimal** Typ.<br /><br /> Der JDBC-Typ **DECIMAL** ist außerdem den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen **money** und **smallmoney** zugeordnet. Dabei handelt es sich um spezielle Dezimaltypen fester Genauigkeit, die in 8 bzw. 4 Byte gespeichert werden. |
  
## <a name="approximate-numeric-types"></a>Angenäherte numerische Typen

Die angenäherten numerischen JDBC-Typen sind **echte**, **doppelte**, und **"float"**.  
  
| Typ   | und Beschreibung                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | Der JDBC-Typ **REAL** weist sieben Ziffern für die Genauigkeit auf (einfache Genauigkeit) und ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **real** zugeordnet.                                                                                                                                     |
| DOUBLE | Der JDBC-Typ **DOUBLE** weist 15 Ziffern für die Genauigkeit auf (doppelte Genauigkeit) und ist dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ **float** zugeordnet. Der JDBC **"float"** Typ ist ein Synonym für **doppelte**. Da zwischen Verwechslungen **"float"** und **doppelte**, **doppelte** wird bevorzugt. |
  
## <a name="datetime-types"></a>Datum-/Zeittypen

Der JDBC **Zeitstempel** Typ zugeordnet werden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **"DateTime"** und **Smalldatetime** Typen. Der Typ **datetime** wird in zwei ganzzahligen Werten mit der Länge 4 Byte gespeichert. Der Typ **smalldatetime** enthält die gleichen Informationen (Datum und Uhrzeit), allerdings mit geringerer Genauigkeit in zwei Integer-Werten mit der Länge 2 Byte.  
  
> [!NOTE]  
> Bei dem Typ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** handelt es sich um einen binären Zeichenfolgentyp mit fester Länge. Ordnet nicht auf eine der JDBC-Typen: **Datum**, **Zeit**, oder **Zeitstempel**.  
  
## <a name="custom-type-mapping"></a>Benutzerdefinierte Typzuordnung

Die Zuordnungsfunktion für benutzerdefinierte Typen von JDBC, die die SQLData-Schnittstellen für die erweiterten JDBC-Typen (UDTs, Struct usw.) verwendet, ist im JDBC-Treiber nicht implementiert.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
