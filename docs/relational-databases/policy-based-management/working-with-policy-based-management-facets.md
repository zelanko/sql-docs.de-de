---
title: Arbeiten mit Facets der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 179b5431f0531b29b4867f405ee88e4567ddb5d8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68054397"
---
# <a name="working-with-policy-based-management-facets"></a>Arbeiten mit Facets der richtlinienbasierten Verwaltung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ein Facet der richtlinienbasierten Verwaltung ist ein Satz von logischen Eigenschaften, die sich auf einen verwaltungsrelevanten Bereich beziehen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst mehrere vordefinierte Facets. Dazu gehört beispielsweise das Facet für die Oberflächenkonfiguration, das die standardmäßig deaktivierten Funktionen als Eigenschaften definiert.  
  
 Wenn Sie viele ähnliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebungen verwalten, können Sie ein Facet für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]konfigurieren, den Status des Facets in eine Datei kopieren und diese Datei anschließend als Richtlinie in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importieren. Sobald der Status in eine Richtlinie umgewandelt wurde, kann die Richtlinie auf andere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Instanzobjekte, Datenbanken oder Datenbankobjekte angewendet werden.  
  
 In diesem Thema wird beschrieben, wie der Status eines Facets in eine XML-Datei kopiert wird.  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Berechtigungen  
 Die Verfahren in diesem Thema erfordern die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="viewing-and-copying-facet-states"></a>Anzeigen und Kopieren von Facet-Status  
 [Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt](../../relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei](../../relational-databases/policy-based-management/copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
