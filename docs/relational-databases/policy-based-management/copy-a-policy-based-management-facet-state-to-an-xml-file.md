---
title: Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 45ebbb2cbbc0e39ee3da54e4b914aff4906df1cc
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125085"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie den Status eines Facets der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in eine XML-Datei in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]kopieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Kopieren eines Facet-Status in eine XML-Datei mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Verfahren in diesem Thema erfordern die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>So kopieren Sie einen Facet-Status in eine XML-Datei  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Instanzobjekt, eine Datenbank oder ein Datenbankobjekt, und klicken Sie dann auf **Facets**.  
  
2.  Klicken Sie im Dialogfeld **Facets anzeigen -**_Objektname_ auf **Aktuellen Status als Richtlinie exportieren**.  
  
3.  Geben Sie im Dialogfeld **Als Richtlinie exportieren** den Pfad und den Namen der Datei ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten (**...**), um die Datei zu suchen, und geben Sie dann den Namen der XML-Datei ein. Weitere Informationen zu den Optionen in diesem Dialogfeld finden Sie unter [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md).  
  
4.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
