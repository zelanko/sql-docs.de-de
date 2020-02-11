---
title: FILESTREAM-Unterstützung (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ff05424d9b8726f21c8c4aa2facd42b87961cc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73760877"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM-Unterstützung (OLE DB)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und Native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client 10,0 unterstützt OLE DB die erweiterte FILESTREAM-Funktion. Weitere Informationen zu dieser Funktion finden Sie [unter FILESTREAM-Unterstützung](../../../relational-databases/native-client/features/filestream-support.md). Beispiele finden Sie unter [FileStream und OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Zum Senden und empfangen von **varbinary (max)** -Werten, die größer als 2 GB sind, verwendet eine Anwendung **DBTYPE_IUNKNOWN** in Parameter-und Ergebnis Bindungen. Für Parameter muss der Anbieter IUnknown:: QueryInterface für ISequentialStream und für Ergebnisse, die ISequentialStream zurückgeben, aufruft.  
  
 Bei OLE DB wird die Überprüfung auf ISequentialStream-Werte gelockert. Wenn *wType* in der **DBBINDING** -Struktur **DBTYPE_IUNKNOWN** wird, kann die Längen Überprüfung entweder durch Weglassen **DBPART_LENGTH** von *dwPart* oder durch Festlegen der Länge der Daten (bei Offset *obLength* im Datenpuffer) auf ~ 0 deaktiviert werden. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  
  
 Diese Änderung wirkt sich auf alle Schnittstellen aus, die Daten übertragen, hauptsächlich IRowset:: GetData, ICommand:: Execute und IRowsetFastLoad:: InsertRow.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
