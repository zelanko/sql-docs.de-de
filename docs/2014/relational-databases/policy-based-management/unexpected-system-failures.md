---
title: Unerwartete Systemfehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3b258af10b9b17e6dd7d3ac2e6b486de99dfe7a7
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43807736"
---
# <a name="unexpected-system-failures"></a>Unerwartete Systemfehler
  Diese Regel überprüft das SYSTEM-Ereignis 6008 im Ereignisprotokoll auf dem Computer. Dieses Ereignis gibt ein unerwartetes Herunterfahren des Systems an. Das System ist möglicherweise instabil und bietet nicht die Stabilität und Integrität, die für das Hosten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erforderlich ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Ermitteln Sie sofort die Ursache der unerwarteten Serverneustarts, oder verschieben Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einen anderen Computer.  
  
  
