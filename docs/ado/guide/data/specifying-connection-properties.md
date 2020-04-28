---
title: Angeben von Verbindungs Eigenschaften | Microsoft-Dokumentation
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
ms.openlocfilehash: 5aee5946f3087956a0117b88f4044ef8a6c9bd9f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924137"
---
# <a name="specifying-connection-properties"></a>Angeben von Verbindungseigenschaften
Sie können einen Großteil der durch eine [Verbindungs Zeichenfolge](../../../ado/guide/data/creating-a-connection-string.md) angegebenen Informationen bereitstellen, indem Sie die Eigenschaften des **Verbindungs** Objekts vor dem Öffnen der Verbindung festlegen. Beispielsweise können Sie denselben Effekt wie die Verbindungs Zeichenfolge erzielen, die unter [Erstellen einer Verbindungs Zeichenfolge](../../../ado/guide/data/creating-a-connection-string.md) mit dem folgenden Code erläutert wird.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase wird erst festgelegt, nachdem Sie die Verbindung geöffnet haben.  
  
> [!NOTE]
>  In ADO dürfen Sie kein Kennwort mit Semikolons (";") verwenden, es sei denn, das Kennwort ist in einfache Anführungszeichen eingeschlossen.
