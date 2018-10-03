---
title: Netzwerkpaketgröße darf 8060 Bytes nicht überschreiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a4e25b746305cc3f8575f167cc9a216491ac55f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126200"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Netzwerkpaketgröße darf 8060 Bytes nicht überschreiten
  Wenn der für sp_configure 'Netzwerkpaketgröße' angegebene Wert oder die Netzwerkpaketgröße eines angemeldeten Benutzers 8060 Bytes überschreitet, führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verschiedene Speicherbelegungsvorgänge aus. Dies kann zu einer Zunahme des virtuellen Adressraums führen, der nicht für den Pufferpool reserviert ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Die Netzwerkpaketgröße sollte 8060 Bytes nicht überschreiten.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Microsoft Knowledge Base-Artikel 903002](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
