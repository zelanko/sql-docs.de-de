---
description: MSSQLSERVER_15599
title: MSSQLSERVER_15599 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eca555fb3ced04a0258db78c89c53e8cef9d9c20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333816"
---
# <a name="mssqlserver_15599"></a>MSSQLSERVER_15599
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|15599|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Meldungstext|Überwachung und Berechtigungen können nicht für lokale temporäre Objekte festgelegt werden.|  
  
## <a name="explanation"></a>Erklärung  
Überwachung und Berechtigungen haben keine Auswirkungen, wenn sie für lokale oder globale temp-Objekte festgelegt werden. Die Anweisungen haben keinem Fehler zur Folge (die Vorgänge geben Erfolg zurück), sie haben lediglich keine Auswirkungen.  
  
Dieses Verhalten hat sich nicht geändert. Seit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wird der Benutzer jedoch in einer Informationsmeldung hierüber informiert.  
  
## <a name="user-action"></a>Benutzeraktion  
Es ist keine Aktion notwendig. Sie sollten jedoch das Entfernen von Anweisungen in Erwägung ziehen, durch die Überwachung oder Berechtigungen für lokale oder globale temp-Objekte festgelegt werden.  
  
