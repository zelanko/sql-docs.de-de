---
title: FILESTREAM-Unterstützung (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba270b26a5a290f5b5c6fdd2830f10b9bf695037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049439"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM-Unterstützung (OLE DB)
  Beginnend mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 unterstützt OLE DB die verbesserte FILESTREAM-Funktion. Weitere Informationen zu diesem Feature finden Sie unter [FILESTREAM-Unterstützung](../features/filestream-support.md). Beispiele finden Sie in [Filestream und OLE DB-](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Um `varbinary(max)`-Werte über 2 GB zu senden und zu empfangen, verwendet eine Anwendung `DBTYPE_IUNKNOWN` in Parameter- und Ergebnisbindungen. Für Parameter muss der Anbieter aufrufen IUnknown:: QueryInterface für ISequentialStream und Ergebnisse, die einer ISequentialStream-Schnittstelle zurückgibt.  
  
 Für OLE DB wird die Option ISequentialStream Werte zur Überprüfung gelockert werden. Wenn *wType* ist `DBTYPE_IUNKNOWN` in der `DBBINDING` Struktur längenüberprüfung kann deaktiviert entweder durch das weglassen `DBPART_LENGTH` aus *DwPart* oder durch Festlegen der Länge der Daten (am Offset *ObLength* im Datenpuffer) auf ~ 0. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  
  
 Diese Änderung wirkt sich auf alle Schnittstellen, die Daten, die hauptsächlich IRowset:: GetData ICommand:: Execute und IRowsetFastLoad:: InsertRow übertragen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  