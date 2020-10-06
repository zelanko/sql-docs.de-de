---
description: Beibehalten von hierarchischen Recordsets
title: Beibehalten hierarchischer Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
author: rothja
ms.author: jroth
ms.openlocfilehash: b3764011c0ce0e3a49a17b20cbb344b5e98218d7
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724951"
---
# <a name="persisting-hierarchical-recordsets"></a>Beibehalten von hierarchischen Recordsets
Sie können ein hierarchisches **Recordset** in einer Datei im ADTG-oder XML-Format speichern, indem Sie die [Save](../../../ado/reference/ado-api/save-method.md) -Methode aufrufen. Es gelten jedoch zwei Einschränkungen beim Speichern hierarchischer **Recordsets**im XML-Format: Sie können XML nicht in XML speichern, wenn das hierarchische **Recordset** ausstehende Updates enthält, und Sie können kein parametrisiertes hierarchisches **Recordset**speichern.  
  
 Weitere Informationen zum Daten Strukturierungs Anbieter finden Sie unter [Microsoft Data Strukturierung Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) und [Übersicht über den Daten Strukturierungs Dienst für OLE DB](/previous-versions/windows/desktop/ms719615(v=vs.85)).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)