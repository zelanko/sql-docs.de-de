---
title: Unerwartete Systemfehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4451b3103281038d383d3e2dda2ab0353ff1b90d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207210"
---
# <a name="unexpected-system-failures"></a>Unerwartete Systemfehler
  Diese Regel überprüft das SYSTEM-Ereignis 6008 im Ereignisprotokoll auf dem Computer. Dieses Ereignis gibt ein unerwartetes Herunterfahren des Systems an. Das System ist möglicherweise instabil und bietet nicht die Stabilität und Integrität, die für das Hosten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erforderlich ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Ermitteln Sie sofort die Ursache der unerwarteten Serverneustarts, oder verschieben Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einen anderen Computer.  
  
  
