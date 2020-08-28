---
description: Angeben von Verbindungseigenschaften
title: Angeben von Verbindungs Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4d3a70388415402db3ecf8bdb21bd717a66aa6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979561"
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
