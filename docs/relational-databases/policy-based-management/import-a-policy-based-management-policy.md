---
title: So importieren Sie eine richtlinienbasierte Verwaltungsrichtlinie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54e0ca12595b0ce8bdde128c9261918c910ffdcf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934346"
---
# <a name="import-a-policy-based-management-policy"></a>Importieren einer Richtlinie der richtlinienbasierten Verwaltung
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie eine Instanz einer Richtlinie der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]importieren.  
  
## <a name="permissions"></a>Berechtigungen
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.

  
##  <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio  
  
### <a name="to-import-a-policy-instance"></a>So importieren Sie eine Richtlinieninstanz  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, in dem sich die neu importierte Richtlinieninstanz befinden wird.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Richtlinien** , und wählen Sie **Richtlinie importieren**aus.  
  
5.  Geben Sie im Dialogfeld **Importieren** den Pfad und den Namen der Datei ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (**…**), um die XML-Datei zu suchen, die die Richtlinie enthält, und wählen Sie dann die Datei aus. Weitere Informationen zu den Optionen im Dialogfeld **Importieren** finden Sie unter [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  Wenn Sie fertig sind, klicken Sie auf **OK**.  


## <a name="example-policies"></a>Beispielrichtlinien
 Beispielrichtlinien sind nicht in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enthalten, jedoch können Sie weiterhin auf zuvor verteilte Beispielrichtlinien zugreifen, indem Sie [SQL Server Management Studio v17](../../ssms/release-notes-ssms.md#previous-ssms-releases) installieren.  Sobald SQL Server Management Studio v17 installiert wurde, finden Sie die Beispielrichtlinien unter `C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Policies`. Diese Richtlinien können importiert und als Grundlage für Ihre eigenen richtlinienbasierten Verwaltungsrichtlinien verwendet werden.
