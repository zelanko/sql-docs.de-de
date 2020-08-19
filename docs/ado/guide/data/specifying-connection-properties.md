---
description: Angeben von Verbindungseigenschaften
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e1f7a26e66eae550bc740f2f9be5a3606650dcb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452832"
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
