---
title: FILESTREAM-Unterstützung (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 925c624139e64b5d3aeb371e5eaf70b0fa1da171
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416959"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM-Unterstützung (OLE DB)
  Beginnend mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 unterstützt OLE DB die verbesserte Funktion FILESTREAM. Weitere Informationen zu diesem Feature finden Sie unter [FILESTREAM-Unterstützung](../features/filestream-support.md). Beispiele finden Sie [Filestream und OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Um `varbinary(max)`-Werte über 2 GB zu senden und zu empfangen, verwendet eine Anwendung `DBTYPE_IUNKNOWN` in Parameter- und Ergebnisbindungen. Für Parameter muss der Anbieter IUnknown:: QueryInterface aufrufen, einer ISequentialStream-Schnittstelle und für Ergebnisse, die einer ISequentialStream-Schnittstelle zurückzugeben.  
  
 Für OLE DB wird überprüfen im Zusammenhang mit ISequentialStream-Werte erhöht. Wenn *wType* ist `DBTYPE_IUNKNOWN` in die `DBBINDING` Struktur längenüberprüfung möglich deaktiviert, entweder durch Auslassen `DBPART_LENGTH` aus *DwPart* oder durch Festlegen der Länge der Daten (bei Offset *ObLength* im Datenpuffer) auf ~ 0. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  
  
 Diese Änderung wirkt sich auf alle Schnittstellen, die Daten, die hauptsächlich IRowset:: GetData ICommand:: Execute und IRowsetFastLoad:: InsertRow übertragen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  
