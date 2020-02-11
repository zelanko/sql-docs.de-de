---
title: Anbieter Unterstützung für ADOX (ADO) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2b07f4563d54254310c08c8c132d0729b8ccdc6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923215"
---
# <a name="provider-support-for-adox-ado"></a>Anbieterunterstützung für ADOX (ADO)
Bestimmte Funktionen von ADOX werden je nach OLE DB Datenanbieter nicht unterstützt. ADOX wird mit dem OLE DB- [Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)vollständig unterstützt. Die nicht unterstützten Funktionen mit dem [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), dem [Microsoft OLE DB-Anbieter für ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)oder dem [Microsoft OLE DB-Anbieter für Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) sind in den folgenden Tabellen aufgeführt. ADOX wird von keinem anderen Anbieter von Microsoft OLE DB unterstützt.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Microsoft OLE DB-Anbieter für SQL Server  
  
|Objekt oder Sammlung|Verwendungs Einschränkung|  
|--------------------------|-----------------------|  
|**Tabellen** Sammlung|Eigenschaften sind vor der Objekt Erstellung Lese-/Schreibzugriff und schreibgeschützt, wenn auf ein vorhandenes Objekt verwiesen wird.|  
|**Views** -Auflistung|**Sichten** werden nicht unterstützt.|  
|**Prozeduren**|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Procedure** -Objekt|Die **Command** -Eigenschaft wird nicht unterstützt.|  
|**Schlüssel** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Benutzer** Sammlung|**Benutzer** werden nicht unterstützt.|  
|**Groups** -Sammlung|**Gruppen** werden nicht unterstützt.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB-Anbieter für ODBC  
  
|Objekt oder Sammlung|Verwendungs Einschränkung|  
|--------------------------|-----------------------|  
|**Catalog** -Objekt|Die **Create** -Methode wird nicht unterstützt.|  
|**Tabellen** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt. Eigenschaften sind vor der Objekt Erstellung Lese-/Schreibzugriff und schreibgeschützt, wenn auf ein vorhandenes Objekt verwiesen wird.|  
|**Prozeduren**|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Procedure** -Objekt|Die **Command** -Eigenschaft wird nicht unterstützt.|  
|**Index** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Schlüssel** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Benutzer** Sammlung|**Benutzer** werden nicht unterstützt.|  
|**Groups** -Sammlung|**Gruppen** werden nicht unterstützt.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB-Anbieter für Oracle  
  
|Objekt oder Sammlung|Verwendungs Einschränkung|  
|--------------------------|-----------------------|  
|**Catalog** -Objekt|Die **Create** -Methode wird nicht unterstützt.|  
|**Tabellen** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt. Eigenschaften sind vor der Objekt Erstellung Lese-/Schreibzugriff und schreibgeschützt, wenn auf ein vorhandenes Objekt verwiesen wird.|  
|**Views** -Auflistung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|Objekt **anzeigen**|Die **Command** -Eigenschaft wird nicht unterstützt.|  
|**Procedures** -Objekt|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Procedure** -Objekt|Die **Command** -Eigenschaft wird nicht unterstützt.|  
|**Index** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Schlüssel** Sammlung|Die **Append** -und **Delete** -Methoden werden nicht unterstützt.|  
|**Benutzer** Sammlung|**Benutzer** werden nicht unterstützt.|  
|**Groups** -Sammlung|**Gruppen** werden nicht unterstützt.|
