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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11ab68775e19ec1d3ce3c888917588f41ad65287
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924639"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Beibehalten von gefilterten und hierarchischen Recordsets
Wenn die [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft gilt für die **Recordset**, nur die Zeilen zugegriffen werden kann, unter dem Filter werden gespeichert. Wenn die **Recordset** hierarchisch aufgebaut ist, der aktuellen untergeordneten **Recordset** und seine untergeordneten Elemente gespeichert werden, einschließlich der übergeordneten **Recordset**. Wenn die **speichern** Methode eines untergeordneten Elements **Recordset** wird aufgerufen, das untergeordnete Element und alle zugehörigen untergeordneten Elemente werden gespeichert, das übergeordnete Element ist jedoch nicht. Weitere Informationen zu hierarchischen **Recordsets**, finden Sie unter [Datenstrukturierung](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Einige Einschränkungen gelten beim Speichern von hierarchischen **Recordsets** (Daten-Shapes) im XML-Format. Weitere Informationen finden Sie unter [beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).
