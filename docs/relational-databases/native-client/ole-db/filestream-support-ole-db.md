---
description: FILESTREAM-Unterstützung (OLE DB)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8dd62a70c60ff1242aa4ea8b81c85e9ae6046ea1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428072"
---
# <a name="filestream-support-ole-db"></a>FILESTREAM-Unterstützung (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0 unterstützt OLE DB die erweiterte FILESTREAM-Funktion. Weitere Informationen zu dieser Funktion finden Sie [unter FILESTREAM-Unterstützung](../../../relational-databases/native-client/features/filestream-support.md). Beispiele finden Sie unter [FILESTREAM und OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Eine Anwendung verwendet **DBTYPE_IUNKNOWN** in Parameter- und Ergebnisbindungen, um **varbinary(max)** -Werte zu senden und zu empfangen, die größer als 2 GB sind. Der Anbieter muss für Parameter IUnknown::QueryInterface für ISequentialStream und für Ergebnisse abrufen, die ISequentialStream zurückgeben.  
  
 Für OLE DB wird die auf ISequentialStream-Werte bezogene Überprüfung gelockert. Wenn *wType* in der **DBBINDING**-Struktur **DBTYPE_IUNKNOWN** ist, kann die Längenüberprüfung deaktiviert werden, indem **DBPART_LENGTH** aus *dwPart* ausgelassen wird oder die Länge der Daten (bei Offset *obLength* im Datenpuffer) auf ~0 festgelegt wird. In diesem Fall überprüft der Provider die Länge des Werts nicht und fordert alle Daten an (oder gibt sie zurück), die über den Datenstrom zur Verfügung stehen. Diese Änderung wird auf alle LOB-Typen (Large Object) und auf XML angewendet, allerdings nur, wenn eine Verbindung zu [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Servern (oder höher) besteht. Auf diese Weise erhalten Entwickler eine höhere Flexibilität, während sie die Konsistenz und Abwärtskompatibilität für vorhandene Anwendungen und Downlevelserver beibehalten.  
  
 Diese Änderung wirkt sich auf alle Schnittstellen aus, die Daten übertragen (hauptsächlich IRowset::GetData, ICommand::Execute und IRowsetFastLoad::InsertRow).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
