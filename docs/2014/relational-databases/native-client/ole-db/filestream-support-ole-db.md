---
title: FILESTREAM-Unterstützung (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f50f002514977f60fb07358293ecbdd524884e58
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704249"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM-Unterstützung (OLE DB)
  Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0 unterstützt OLE DB die erweiterte FILESTREAM-Funktion. Weitere Informationen zu dieser Funktion finden Sie [unter FILESTREAM-Unterstützung](../features/filestream-support.md). Beispiele finden Sie unter [FILESTREAM und OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Um `varbinary(max)`-Werte über 2 GB zu senden und zu empfangen, verwendet eine Anwendung `DBTYPE_IUNKNOWN` in Parameter- und Ergebnisbindungen. Der Anbieter muss für Parameter IUnknown::QueryInterface für ISequentialStream und für Ergebnisse abrufen, die ISequentialStream zurückgeben.  
  
 Für OLE DB wird die auf ISequentialStream-Werte bezogene Überprüfung gelockert. Wenn sich *wType* `DBTYPE_IUNKNOWN` in der `DBBINDING` Struktur befindet, kann die Längen Überprüfung entweder durch Weglassen `DBPART_LENGTH` von *dwPart* oder durch Festlegen der Länge der Daten (bei Offset *obLength* im Datenpuffer) auf ~ 0 deaktiviert werden. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  
  
 Diese Änderung wirkt sich auf alle Schnittstellen aus, die Daten übertragen (hauptsächlich IRowset::GetData, ICommand::Execute und IRowsetFastLoad::InsertRow).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung für SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  
