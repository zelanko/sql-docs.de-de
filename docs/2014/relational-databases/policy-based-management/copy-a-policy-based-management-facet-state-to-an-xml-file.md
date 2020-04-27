---
title: Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3cae39c440c86348763b20ae04c70b3ce2ecc181
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62667345"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei
  In diesem Thema wird beschrieben, wie Sie den Status eines Facets der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in eine XML-Datei in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]kopieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Kopieren eines Facet-Status in eine XML-Datei mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Verfahren in diesem Thema erfordern die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>So kopieren Sie einen Facet-Status in eine XML-Datei  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Instanzobjekt, eine Datenbank oder ein Datenbankobjekt, und klicken Sie dann auf **Facets**.  
  
2.  Klicken Sie im Dialogfeld **Facetten anzeigen-**_object_name_ auf **aktuellen Status als Richtlinie exportieren**.  
  
3.  Geben Sie im Dialogfeld **Als Richtlinie exportieren** den Pfad und den Namen der Datei ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten (**...**), um die Datei zu suchen, und geben Sie dann den Namen der XML-Datei ein. Weitere Informationen zu den Optionen in diesem Dialogfeld finden Sie unter [Export As Policy Dialog Box](export-as-policy-dialog-box.md).  
  
4.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
