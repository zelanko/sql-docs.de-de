---
description: Beibehalten von gefilterten und hierarchischen Recordsets
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
ms.openlocfilehash: a69b491f4bb5834331b9cfa582b6f72d248ba317
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453062"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Beibehalten von gefilterten und hierarchischen Recordsets
Wenn die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für das **Recordset**wirksam ist, werden nur die Zeilen gespeichert, auf die der Filter zugreifen kann. Wenn das **Recordset** hierarchisch ist, werden das aktuelle untergeordnete **Recordset** und seine untergeordneten Elemente gespeichert, einschließlich des übergeordneten **Recordsets**. Wenn die **Save** -Methode eines untergeordneten **Recordsets** aufgerufen wird, werden das untergeordnete Element und alle zugehörigen untergeordneten Elemente gespeichert, das übergeordnete Element ist jedoch nicht. Weitere Informationen zu hierarchischen **Recordsets**finden Sie unter [Daten Strukturierung](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Es gelten einige Einschränkungen, wenn Sie hierarchische **Recordsets** (Daten Formen) im XML-Format speichern. Weitere Informationen finden Sie unter Beibehalten von [Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).
