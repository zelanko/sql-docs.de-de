---
title: SQLXML ist in SQLServer nicht installiert. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d321a6eb5c0f6735507158be581ed0a01878fbb9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222900"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML ist in SQL Server nicht installiert
  Vor der Veröffentlichung von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wurde SQLXML 4.0 mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veröffentlicht und war Bestandteil der Standardinstallation aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen außer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ist die neueste Version von SQLXML (SQLXML 4.0 SP1) nicht mehr in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten. Um SQLXML 4.0 SP1 installieren, sobald diese verfügbar ist, laden Sie sie aus [Install Location for SQLXML SP1](http://www.microsoft.com/download/details.aspx?id=3522).  
  
 Wenn eine Anwendung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und SQLXML 4.0 erfordert und auf dem Computer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] nicht installiert ist, müssen Sie SQLXML 4.0 SP1 herunterladen und installieren.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Verhalten von SQLXML 4.0 SP1 mit neuen Datentypen, die SQLOLEDB und SQL Server Native Client-OLE DB-Anbieter verwenden  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] führt die folgenden Datentypen, die die Entwicklern, die Verwendung von SQLXML verwenden möchten:  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 Bei Verwendung von SQLXML 4.0 SP1 mit SQLOLEDB (in Windows Data Access Components, früher Microsoft Data Access Components) oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], diese neuen Typen als Zeichenfolgen an einen Entwickler angezeigt. SQLXML 4.0 SP1 aktiviert diese vier neuen Datentypen als integrierte skalare Typen, die bei der Verwendung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter 11.0. Wenn Sie SQLXML 4.0 SP1 noch nicht heruntergeladen haben, kann die Zuordnung dieser Typen zu anderen als Zeichenfolgentypen zum Abschneiden einiger Daten führen. Z. B. das zuordnen `DateTime2` zu `xsd:date` zum Abschneiden von Daten führt dazu, dass die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` -Genauigkeit von 3,33 Millisekunden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLXML 4.0-Programmierkonzepte](sqlxml-4-0-programming-concepts.md)  
  
  
