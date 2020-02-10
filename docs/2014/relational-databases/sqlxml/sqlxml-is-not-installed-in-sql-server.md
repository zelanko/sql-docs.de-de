---
title: SQLXML ist nicht in SQL Server installiert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8fe1d4b937e5972eb90e567ded91f7a23af577d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012160"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML ist in SQL Server nicht installiert
  Vor der Veröffentlichung von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]wurde SQLXML 4.0 mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veröffentlicht und war Bestandteil der Standardinstallation aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen außer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ist die neueste Version von SQLXML (SQLXML 4.0 SP1) nicht mehr in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten. Um SQLXML 4,0 SP1 zu installieren, wenn es verfügbar ist, laden Sie es vom [Installationsort für SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=16978)herunter.  
  
 Wenn eine Anwendung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und SQLXML 4.0 erfordert und auf dem Computer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] nicht installiert ist, müssen Sie SQLXML 4.0 SP1 herunterladen und installieren.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Verhalten von SQLXML 4.0 SP1 mit neuen Datentypen, die SQLOLEDB und SQL Server Native Client-OLE DB-Anbieter verwenden  
 Mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] werden die folgenden Datentypen eingeführt, die von SQLXML-Entwicklern verwendet werden können:  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 Bei Verwendung von SQLXML 4.0 SP1 mit SQLOLEDB (in Windows Data Access Components, früher Microsoft Data Access Components) oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] werden diese neuen Typen Entwicklern als Zeichenfolgen angezeigt. SQLXML 4.0 SP1 aktiviert diese vier neuen Datentypen als integrierte skalare Typen, wenn diese mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter 11.0 verwendet werden. Wenn Sie SQLXML 4.0 SP1 noch nicht heruntergeladen haben, kann die Zuordnung dieser Typen zu anderen als Zeichenfolgentypen zum Abschneiden einiger Daten führen. Beispielsweise führt die `DateTime2` Zuordnung `xsd:date` zu dazu, dass die Daten auf die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` Genauigkeit von 3,33 Millisekunden gekürzt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLXML 4.0-Programmierkonzepte](sqlxml-4-0-programming-concepts.md)  
  
  
