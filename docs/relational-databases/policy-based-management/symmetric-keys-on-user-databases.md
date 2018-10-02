---
title: Symmetrische Schlüssel für Benutzerdatenbanken | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 213ae962f1dbc45d9e6fc2bed67c94f2eafb1183
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601738"
---
# <a name="symmetric-keys-on-user-databases"></a>Symmetrische Schlüssel für Benutzerdatenbanken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft, ob Schlüssel mit einer Länge von weniger als 128 Bytes den RC2- oder RC4-Verschlüsselungsalgorithmus verwenden.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Verwenden Sie die AES-128-Bit-Verschlüsselung oder eine stärkere Verschlüsselung, um symmetrische Schlüssel für die Datenverschlüsselung zu erstellen. Wenn AES nicht vom Betriebssystem unterstützt wird, verwenden Sie 3DES.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
