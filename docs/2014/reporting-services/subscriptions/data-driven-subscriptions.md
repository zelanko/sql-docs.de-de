---
title: Datengesteuerte Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90733af47898116236d94c9b9f6ccc6d9fc542ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66100869"
---
# <a name="data-driven-subscriptions"></a>Datengesteuerte Abonnements
  Ein datengesteuertes Abonnement bietet eine Möglichkeit, dynamische Abonnementdaten zu verwenden, die zur Laufzeit aus einer externen Datenquelle abgerufen werden. Mit einem datengesteuerten Abonnement können auch statischer Text und Standardwerte verwendet werden, die Sie beim Definieren des Abonnements angeben. Sie können datengesteuerte Abonnements für die folgenden Aufgaben verwenden:  
  
-   Verteilen eines Berichts an eine ständig wechselnde Liste von Abonnenten. Beispielsweise können Sie mit datengesteuerten Abonnements einen Bericht in einer großen Organisation verteilen, in der die Abonnenten von Monat zu Monat variieren. Sie können aber auch sonstige Kriterien verwenden, um die Gruppenmitgliedschaft aus einer Gruppe vorhandener Benutzer zu bestimmen.  
  
-   Filtern der Berichtsausgabe mithilfe von zur Laufzeit abgerufenen Berichtsparameterwerten.  
  
-   Ändern der Berichtsausgabeformate und Übermittlungsoptionen für jede Berichtsübermittlung.  
  
 Ein datengesteuertes Abonnement besteht aus mehreren Teilen. Die festen Komponenten eines datengesteuerten Abonnements werden beim Erstellen des Abonnements definiert. Dazu zählen u. a. die folgenden:  
  
-   Der Bericht, für den das Abonnement definiert wurde (ein Abonnement ist immer einem einzelnen Bericht zugeordnet).  
  
-   Die Übermittlungserweiterung, die zum Verteilen des Berichts verwendet wurde. Sie können die E-Mail-Übermittlungserweiterung des Berichtsservers, eine Dateifreigabe-Übermittlungserweiterung, den NULL-Übermittlungsanbieter zum Vorabladen des Caches oder eine benutzerdefinierte Übermittlungserweiterung angeben. Innerhalb eines einzelnen Abonnements können Sie nicht mehrere Übermittlungserweiterungen angeben.  
  
-   Die Abonnentendatenquelle. Sie müssen beim Definieren des Abonnements eine Verbindungszeichenfolge für die Datenquelle mit Abonnentendaten angeben. Die Abonnentendatenquelle kann nicht dynamisch zur Laufzeit angegeben werden.  
  
-   Beim Definieren des Abonnements muss die zum Auswählen von Abonnentendaten verwendete Abfrage angegeben werden. Sie können die Abfrage zur Laufzeit nicht ändern.  
  
 Die in einem datengesteuerten Abonnement verwendeten dynamischen Daten werden abgerufen, wenn das Abonnement verarbeitet wird. Beispiele für Daten, die Sie in einem Abonnement verwenden können, sind der Abonnentenname, die E-Mail-Adresse, das bevorzugte Berichtsausgabeformat oder beliebige Werte, die für Berichtsparameter gültig sind. Sie können in einem datengesteuerten Abonnement dynamische Werte verwenden, wenn Sie Sie eine Zuordnung zwischen den bei einer Abfrage zurückgegebenen Feldern und bestimmten Übermittlungsoptionen sowie Berichtsparametern definieren. Bei der Verarbeitung des Abonnements werden jeweils variable Daten aus einer Abonnentendatenquelle abgerufen.  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a>Anforderungen für die Verwendung datengesteuerter Abonnements  
 Die Funktion für datengesteuerte Abonnements ist nicht in allen Editionen verfügbar. Zudem bestehen Einschränkungen hinsichtlich der Arten von Datenquellen, die Sie zur Laufzeit zum Abrufen von Abonnementdaten verwenden können. Die folgende Liste enthält weitere Informationen zu den Anforderungen:  
  
-   Weitere Informationen zu den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Funktion für datengesteuerte Abonnements unterstützen, finden Sie unter [von den-Editionen unterstützte Funktionen SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473)).  
  
-   Wählen Sie für Abonnementdaten eine Datenquelle aus, die Schemainformationen für den Berichtsserver bereitstellen kann. Beispiele für unterstützte Datenquellen Typen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind relationale Daten, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Oracle- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Datenbanken,-Paketdaten, ODBC-Datenquellen und OLE DB Datenquellen. Weitere Informationen zu den Anforderungen an Abonnentendatenquellen finden Sie unter [Verwenden einer externen Datenquelle für Abonnentendaten &#40;datengesteuertes Abonnement&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
## <a name="working-with-data-driven-subscriptions"></a>Arbeiten mit datengesteuerten Abonnements  
 Die folgenden Themen enthalten weitere Informationen zu datengesteuerten Abonnements.  
  
|Themen|BESCHREIBUNG|  
|------------|-----------------|  
|[Erstellen, Ändern und Löschen eines datengesteuerten Abonnements](data-driven-subscriptions.md)|Erläutert das Erstellen, Ändern oder Löschen eines datengesteuerten Abonnements.|  
|[Verwenden Sie eine externe Datenquelle für Abonnentendaten &#40;datengesteuerten Abonnements&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|Enthält Informationen zu den Datenquellen, die Sie für ein datengesteuertes Abonnement verwenden können.|  
|[Erstellen eines datengesteuerten Abonnements &#40;SSRS-Lernprogramm&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)|Enthält schrittweise Anleitungen zum Erstellen eines datengesteuerten Abonnements.|  
|[Zwischenspeichern von Berichten &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)|Beschreibt die Verwendung des NULL-Übermittlungsanbieters mit einem datengesteuerten Abonnement, um den Cache vorab zu laden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Erstellen einer datengesteuerten Abonnementseite &#40;Berichts-Manager&#41;](../create-data-driven-subscription-page-report-manager.md)   
 [&#40;Berichts-Manager vorab laden&#41;](../report-server/preload-the-cache-report-manager.md)  
  
  
