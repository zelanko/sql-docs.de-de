---
title: Beibehalten von gefilterten und hierarchischen Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fa3fdd55fb78f16629907c174b08aab64ceb86e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763111"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Beibehalten von gefilterten und hierarchischen Recordsets
Wenn die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für das **Recordset**wirksam ist, werden nur die Zeilen gespeichert, auf die der Filter zugreifen kann. Wenn das **Recordset** hierarchisch ist, werden das aktuelle untergeordnete **Recordset** und seine untergeordneten Elemente gespeichert, einschließlich des übergeordneten **Recordsets**. Wenn die **Save** -Methode eines untergeordneten **Recordsets** aufgerufen wird, werden das untergeordnete Element und alle zugehörigen untergeordneten Elemente gespeichert, das übergeordnete Element ist jedoch nicht. Weitere Informationen zu hierarchischen **Recordsets**finden Sie unter [Daten Strukturierung](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Es gelten einige Einschränkungen, wenn Sie hierarchische **Recordsets** (Daten Formen) im XML-Format speichern. Weitere Informationen finden Sie unter Beibehalten von [Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).
