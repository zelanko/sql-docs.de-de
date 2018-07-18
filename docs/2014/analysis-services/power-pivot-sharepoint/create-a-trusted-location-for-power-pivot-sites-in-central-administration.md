---
title: Erstellen ein vertrauenswürdiges Speicherorts für PowerPivot-Websites in der Zentraladministration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5661842742c4f0f80b56186704a6b9ac967e8db8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153331"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a>Erstellen eines vertrauenswürdigen Speicherorts für PowerPivot-Websites in der Zentraladministration
  In Excel Services können Sie angeben, welche Speicherorte gültige Repositorys für Arbeitsmappen sind, die Sie auf einem SharePoint-Server öffnen. Diese Speicherorte werden als 'vertrauenswürdige Speicherorte' bezeichnet, und Sie können unterschiedliche Konfigurationseinstellungen für jeden vertrauenswürdigen Speicherort verwenden, den Sie erstellen. Bei einer Bereitstellung von PowerPivot für SharePoint sollten Sie erwägen, einen vertrauenswürdigen Speicherort für Sites zu erstellen, die PowerPivot-Arbeitsmappen enthalten, sodass Sie die Einstellungen anwenden können, die optimal für den PowerPivot-Datenzugriff geeignet sind, aber gleichzeitig die Standardeinstellungen für den Rest der Farm beibehalten können.  
  
  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie müssen Farm- oder Dienstadministrator sein, um eine URL als vertrauenswürdigen Speicherort festzulegen.  
  
 Sie müssen die URL-Adresse der SharePoint-Website kennen, die den PowerPivot-Katalog oder eine andere Bibliothek enthält, in der die Arbeitsmappen gespeichert sind. Um die Adresse zu erhalten, öffnen Sie die Website, die die Bibliothek enthält, mit der rechten Maustaste **PowerPivot-Katalog**Option **Eigenschaften**, und kopieren Sie im ersten Teil der Adresse (URL), die den Servernamen und die Website enthält der Pfad.  
  
##  <a name="overview"></a> Übersicht  
 Erste Installationen von Excel Services geben 'http://' als vertrauenswürdigen Speicherort an, was bedeutet, dass Arbeitsmappen von jeder beliebigen Website in der Farm auf dem Server geöffnet werden können. Wenn Sie eine bessere Kontrolle darüber benötigen, welche Speicherorte als vertrauenswürdig angesehen werden, können Sie neue, vertrauenswürdige Speicherorte erstellen, die bestimmten Websites in der Farm zugeordnet sind, und dann die Einstellungen und Berechtigungen für jede einzelne variieren.  
  
 Wenn Sie für den übrigen Teil der Farm Standardwerte beibehalten, gleichzeitig aber andere Einstellungen anwenden möchten, die optimal für den PowerPivot-Datenzugriff geeignet sind, empfiehlt es sich, einen neuen vertrauenswürdigen Speicherort für Websites zu erstellen, die als Host für PowerPivot-Arbeitsmappen dienen. Ein vertrauenswürdiger Speicherort, der für PowerPivot-Arbeitsmappen optimiert ist, könnte z. B. eine maximale Arbeitsmappengröße von 50 MB haben, während der Rest der Farm den Standardwert 10 MB verwendet.  
  
 Das Erstellen eines vertrauenswürdigen Speicherorts wird empfohlen, wenn Sie PowerPivot-Katalogbibliotheken verwenden, um eine Vorschau veröffentlichter Arbeitsmappen anzuzeigen, und Ihnen anstelle des erwarteten Vorschaubilds Datenaktualisierungswarnungen angezeigt werden. Der PowerPivot-Katalog rendert Miniaturbilder von Berichten und Arbeitsmappen unter Verwendung von Daten und Präsentationsinformationen innerhalb des Dokuments. Wenn Beim Aktualisieren warnen für einen vertrauenswürdigen Speicherort aktiviert ist, verfügt der PowerPivot-Katalog möglicherweise nicht über ausreichende Berechtigungen zum Ausführen der Aktualisierung, sodass anstelle des Miniaturbilds ein Fehler angezeigt wird. Das Hinzufügen einer Website als neuer vertrauenswürdiger Speicherort, die den PowerPivot-Katalog enthält, kann dieses Problem ausschließen.  
  
##  <a name="create"></a> Erstellen eines vertrauenswürdigen Speicherorts für PowerPivot-Datenzugriff  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf die Excel Services-Dienstanwendung.  
  
3.  Klicken Sie auf **Vertrauenswürdige Dateispeicherorte**.  
  
4.  Klicken Sie auf **Vertrauenswürdigen Dateispeicherort hinzufügen**.  
  
5.  Geben Sie die URL einer Website ein, in der eine PowerPivot-Katalogbibliothek enthalten ist.  
  
6.  Wählen Sie als Speicherorttyp **Microsoft SharePoint Foundation**aus.  
  
    > [!IMPORTANT]  
    >  UNC- und HTTP-Speicherorttypen werden beim PowerPivot-Datenzugriff nicht unterstützt.  
  
7.  Akzeptieren Sie die Standardeinstellungen für sämtliche Eigenschaften unter Sitzungsverwaltung, Arbeitsmappeneigenschaften und Berechnungsverhalten.  
  
8.  Legen Sie in Arbeitsmappeneigenschaften die Option **Maximale Arbeitsmappengröße** auf **50**fest. Dadurch wird die Obergrenze der Arbeitsmappendateigröße auf die Obergrenze für Dateiuploads in die übergeordnete Webanwendung eingestellt. Wenn die Arbeitsmappen größer als 50 MB sind, müssen Sie die maximale Dateigröße weiter erhöhen. Weitere Informationen finden Sie unter [konfigurieren maximale Dateiuploadgröße &#40;PowerPivot für SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
9. Überprüfen Sie in „Externe Daten“, ob „Externe Daten zulassen“ auf **Vertrauenswürdige Datenverbindungsbibliotheken und eingebettete Verbindungen**festgelegt ist. Diese Einstellung ist für den PowerPivot-Datenzugriff in einer Arbeitsmappe erforderlich.  
  
10. Deaktivieren Sie in „Externe Daten“ für „Beim Aktualisieren warnen“ auch das Kontrollkästchen **Aktualisierungswarnung aktiviert**. Wenn Sie das Kontrollkästchen deaktivieren, kann der PowerPivot-Katalog Routinewarnmeldungen umgehen und stattdessen Vorschaubilder einer Arbeitsmappe anzeigen.  
  
11. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Katalog](../../2014-toc/books-online-for-sql-server-2014.md)   
 [Erstellen und Anpassen von PowerPivot-Katalog](create-and-customize-power-pivot-gallery.md)   
 [Verwenden des PowerPivot-Katalogs](use-power-pivot-gallery.md)  
  
  
