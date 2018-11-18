---
title: Netzwerkpaketgröße darf 8060 Bytes nicht überschreiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b74d7122f6247d4aebfb4046cfe80cbce11897d7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668689"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Netzwerkpaketgröße darf 8060 Bytes nicht überschreiten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn der für sp_configure 'Netzwerkpaketgröße' angegebene Wert oder die Netzwerkpaketgröße eines angemeldeten Benutzers 8060 Bytes überschreitet, führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verschiedene Speicherbelegungsvorgänge aus. Dies kann zu einer Zunahme des virtuellen Adressraums führen, der nicht für den Pufferpool reserviert ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Die Netzwerkpaketgröße sollte 8060 Bytes nicht überschreiten.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Microsoft Knowledge Base-Artikel 903002](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
