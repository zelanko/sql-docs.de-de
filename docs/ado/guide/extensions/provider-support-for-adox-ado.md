---
title: Anbieterunterstützung für ADOX (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6f346779d3a4c8cb43e2b30347ebf6b198d9015
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803278"
---
# <a name="provider-support-for-adox-ado"></a>Anbieterunterstützung für ADOX (ADO)
Bestimmte Features des ADOX werden nicht unterstützt, je nach Ihrer OLE DB-Datenanbieter. ADOX wird vollständig unterstützt, mit der [OLE DB-Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Nicht unterstützten Funktionen mit den [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), [Microsoft OLE DB-Anbieter für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), oder die [Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) sind in den folgenden Tabellen aufgeführt. ADOX wird nicht von anderen Microsoft OLE DB-Anbietern unterstützt.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Microsoft OLE DB-Anbieter für SQLServer  
  
|Objekt oder einer Auflistung|Nutzungseinschränkung|  
|--------------------------|-----------------------|  
|**Tabellen** Auflistung|Eigenschaften sind Lese-/Schreibzugriff vor dem Erstellen von Objekten, und schreibgeschützt, wenn Sie ein vorhandenes Objekt zu verweisen.|  
|**Ansichten** Auflistung|**Ansichten** wird nicht unterstützt.|  
|**Prozeduren** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Prozedur** Objekt|Die **Befehl** Eigenschaft wird nicht unterstützt.|  
|**Schlüssel** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Benutzer** Auflistung|**Benutzer** wird nicht unterstützt.|  
|**Gruppen** Auflistung|**Gruppen** wird nicht unterstützt.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB-Anbieter für ODBC  
  
|Objekt oder einer Auflistung|Nutzungseinschränkung|  
|--------------------------|-----------------------|  
|**Katalog** Objekt|Die **erstellen** Methode wird nicht unterstützt.|  
|**Tabellen** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt. Eigenschaften sind Lese-/Schreibzugriff vor dem Erstellen von Objekten, und schreibgeschützt, wenn Sie ein vorhandenes Objekt zu verweisen.|  
|**Prozeduren** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Prozedur** Objekt|Die **Befehl** Eigenschaft wird nicht unterstützt.|  
|**Indizes** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Schlüssel** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Benutzer** Auflistung|**Benutzer** wird nicht unterstützt.|  
|**Gruppen** Auflistung|**Gruppen** wird nicht unterstützt.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB-Anbieter für Oracle  
  
|Objekt oder einer Auflistung|Nutzungseinschränkung|  
|--------------------------|-----------------------|  
|**Katalog** Objekt|Die **erstellen** Methode wird nicht unterstützt.|  
|**Tabellen** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt. Eigenschaften sind Lese-/Schreibzugriff vor dem Erstellen von Objekten, und schreibgeschützt, wenn Sie ein vorhandenes Objekt zu verweisen.|  
|**Ansichten** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Ansicht** Objekt|Die **Befehl** Eigenschaft wird nicht unterstützt.|  
|**Prozeduren** Objekt|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Prozedur** Objekt|Die **Befehl** Eigenschaft wird nicht unterstützt.|  
|**Indizes** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Schlüssel** Auflistung|Die **Append** und **löschen** Methoden werden nicht unterstützt.|  
|**Benutzer** Auflistung|**Benutzer** wird nicht unterstützt.|  
|**Gruppen** Auflistung|**Gruppen** wird nicht unterstützt.|
