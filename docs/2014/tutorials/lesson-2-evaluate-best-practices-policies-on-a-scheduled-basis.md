---
title: 'Lektion 2: Auswerten von Best Practices-Richtlinien auf Basis eines Zeitplans | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd4874e722c12813eb574d94c073cc069f72a4b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148951"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a>Lektion 2: Auswerten von Best Practices-Richtlinien auf der Basis eines Zeitplans
  Sie können geplante Auswertungen von Best Practices-Richtlinien für mindestens eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] konfigurieren. Damit Best Practices-Richtlinien basierend auf einem Zeitplan ausgeführt werden können, müssen Sie die Richtlinien in die Zielinstanz importieren.  
  
 Um geplante Richtlinien auf mehreren Servern bereitzustellen, können Sie die Richtlinien in eine Instanz importieren, die Zeitpläne für jede Richtlinie konfigurieren, die geplanten Richtlinien in einen Ordner exportieren und die geplanten Richtlinien dann über registrierte Server auf den Zielinstanzen bereitstellen.  
  
> [!IMPORTANT]  
>  Auf den Zielinstanzen muss [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ausgeführt werden. Die Automatisierung erfordert, dass die Richtlinien lokal auf einer Instanz gespeichert werden. Dies wird von älteren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Versionen vor [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]nicht unterstützt.  
  
 In dieser Lektion führen Sie die folgenden Schritte aus:  
  
-   Importieren der Best Practices-Richtlinien in eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Konfigurieren der Richtlinien für die Ausführung auf Grundlage eines Zeitplans.  
  
-   Bereitstellen der geplanten Best Practices-Richtlinien auf mehreren Instanzen über registrierte Server.  
  
 Diese Lektion enthält die folgenden Themen:  
  
-   [Importieren der Richtlinien auf eine einzelne Instanz](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [Planen der Richtlinien](../../2014/tutorials/schedule-the-policies.md)  
  
-   [Bereitstellen geplanter Richtlinien auf mehreren Instanzen](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  