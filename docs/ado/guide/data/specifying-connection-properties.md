---
title: Angeben von Verbindungseigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 659701a984a675418b8654e9f747efe5d9e07762
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700324"
---
# <a name="specifying-connection-properties"></a>Angeben von Verbindungseigenschaften
Können Sie angeben, Großteil der Informationen, die gemäß einer [Verbindungszeichenfolge](../../../ado/guide/data/creating-a-connection-string.md) durch Festlegen der Eigenschaften der **Verbindung** Objekt vor dem Öffnen der Verbindung. Sie können z. B. dieselbe Wirkung erzielen, wie in die Verbindungszeichenfolge erläutert [Erstellen einer Verbindungszeichenfolge](../../../ado/guide/data/creating-a-connection-string.md) mithilfe des folgenden Codes.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase festgelegt ist, nur nach dem Öffnen der Verbindung.  
  
> [!NOTE]
>  In ADO verwenden, müssen Sie kein Kennwort mit Semikolons (";"), wenn das Kennwort in einfache Anführungszeichen eingeschlossen ist.
