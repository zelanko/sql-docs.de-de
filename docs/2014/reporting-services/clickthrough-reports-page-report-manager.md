---
title: Berichte mit durchklicken (Seite) (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.modelproperties.drilthroughreports.f1
ms.assetid: e96cdeba-452b-45a8-9bcf-b75d76261e31
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0e9deeb0187814b89a4445ae13edaf9e1e5a5a16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046619"
---
# <a name="clickthrough-reports-page-report-manager"></a>Berichte mit Durchklicken (Seite) (Berichts-Manager)
  Ein Bericht mit Durchklicken zeigt eine Tabelle verknüpfter Daten an, wenn Sie auf die interaktiven Daten klicken, die in Ihrem Bericht enthalten sind. Diese Berichte werden vom Berichtsserver anhand der Informationen generiert, die in dem Modell enthalten sind, den Sie zum Erstellen des Berichts verwendet haben. Wenn Sie die Berichte mit Durchklicken, die der Berichtsserver generiert, nicht verwenden möchten, können Sie benutzerdefinierte Berichte erstellen und auf einem Berichtsserver veröffentlichen. Ordnen Sie dann diese Berichte den interaktiven Datenpunkten zu, die im Modell definiert sind. Die benutzerdefinierten Berichte müssen im Berichts-Generator aus dem gleichen Modell erstellt und dann auf einem Berichtsserver veröffentlicht werden. Verwenden Sie die Seite Berichte mit Durchklicken im Berichts-Manager, um die benutzerdefinierte Berichte Elementen im Modell zuzuordnen.  
  
 Die Seite Berichte mit Durchklicken bietet Ihnen die Möglichkeit, vordefinierte, veröffentlichte Berichts-Generatorberichte bestimmten Entitäten, Ordnern und Elementen in einem Modell zuzuordnen. Wenn Sie einen Bericht einem Element in einem Modell zuordnen, erhalten Benutzer, die zu diesem Element navigieren, den benutzerdefinierten Bericht anstelle eines vom Berichtsserver generierten temporären Berichts.  
  
 Wenn Sie mit benutzerdefinierten Berichten arbeiten, sollten Sie sowohl eine Einzelinstanz- als auch eine Mehrfachinstanzversion des Berichts erstellen. Der Datenpfad, über den ein Benutzer zu einer bestimmten Entität navigiert, bestimmt, ob den Benutzern bei der Ausführung ein Einzelinstanz- oder ein Mehrfachinstanzbericht angezeigt wird. Es ist nicht immer im Vorfeld möglich zu wissen, ob eine bestimmte Version des Berichts nicht erforderlich ist.  
  
 Benutzerdefinierte Berichte, die Sie Entitäten zuordnen, sind über die Ordnerhierarchie des Berichtsservers gesichert. Wenn Sie ein Modellelement einem Bericht zuordnen und der Bericht für einen Benutzer, der dorthin navigiert, nicht verfügbar ist, dann erhält der Benutzer einen von dem Berichtsserver generierten temporären Bericht anstelle des von Ihnen vorgesehenen benutzerdefinierten Berichts.  
  
 Auch wenn es möglich ist, alle Berichte auszuwählen, auf die Sie zugreifen können, sollten Sie nur die Berichte auswählen, die speziell für das von Ihnen konfigurierte Modell erstellt wurden.  
  
> [!NOTE]  
>  Durchklickberichte sind nicht in jeder Edition von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Wenn Sie nicht genau wissen, welche Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Ihrer Organisation verwendet wird, sollten Sie sich mit dem Datenbankadministrator in Verbindung setzen.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-clickthrough-reports-page"></a>So öffnen Sie die Seite "Berichte mit Durchklicken"  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie das Modell, für das Sie Berichte mit Durchklicken zu Entitäten im Modell zuordnen möchten.  
  
2.  Zeigen Sie auf das Modell, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite **Allgemeine Eigenschaften** für das Modell geöffnet.  
  
4.  Wählen Sie die Registerkarte **Durchklicken** aus.  
  
## <a name="options"></a>Tastatur  
 **Modellelementhierarchie**  
 Zeigt die im Modellnamespace enthaltenen Entitäten, Ordner und Elemente an, für die Sie einen benutzerdefinierten Bericht bereitstellen können.  
  
 **Einzelinstanzbericht**  
 Gibt an, welcher benutzerdefinierte Bericht verwendet wird, wenn die Benutzernavigation eine Sicht von Einzelinstanzdaten erforderlich macht. Klicken Sie auf die Schaltfläche zum Durchsuchen, um den gewünschten Bericht auszuwählen.  
  
 **Bericht mit mehreren Instanzen**  
 Gibt an, welcher benutzerdefinierte Bericht verwendet wird, wenn die Benutzernavigation eine Sicht von Mehrfachinstanzdaten erforderlich macht. Klicken Sie auf die Schaltfläche zum Durchsuchen, um den gewünschten Bericht auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Berichten](../../2014/reporting-services/publish-reports.md)  
  
  