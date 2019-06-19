---
title: Zwischenspeichern (Seite), freigegebene Datasets (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae18d021465a7d14ea22b56534ea48ac316154c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109909"
---
# <a name="caching-page-shared-datasets-report-manager"></a>Zwischenspeichern (Seite), Freigegebene Datasets (Berichts-Manager)
  Verwenden Sie die Eigenschaftenseite Zwischenspeichern, um die Cacheoptionen für ein freigegebenes Dataset festzulegen.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a>So öffnen Sie die Eigenschaftenseite "Zwischenspeichern" für ein freigegebenes Dataset  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Eigenschaften freigegebener Datasets konfigurieren möchten.  
  
2.  Zeigen Sie auf das freigegebene Dataset, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie in der Dropdownliste auf **Verwalten**. Die Seite Allgemeine Eigenschaften für den Bericht wird geöffnet.  
  
4.  Klicken Sie auf die Registerkarte **Zwischenspeichern** .  
  
## <a name="options"></a>Optionen  
 **Freigegebenes Dataset Zwischenspeichern**  
 Speichert eine temporäre Kopie der Daten in einem Cache, sobald ein Benutzer erstmalig einen Bericht öffnet, der das freigegebene Dataset verwendet. Nachfolgende Benutzer, die den Bericht innerhalb des Zeitraums der Zwischenspeicherung ausführen, erhalten die zwischengespeicherte Kopie der Daten. Die Zwischenspeicherung erhöht in der Regel die Leistung, da die Daten aus dem Cache zurückgegeben werden und die Datasetabfrage nicht erneut ausgeführt werden muss.  
  
 **Cacheablauf nach dieser Anzahl von Minuten**  
 Geben Sie die Zeitdauer in Minuten an, während derer die zwischengespeicherte Kopie der Daten erhalten bleibt. Sobald eine temporäre Kopie abgelaufen ist, werden die Daten nicht mehr aus dem Cache zurückgegeben. Wenn ein Benutzer einen Bericht, der dieses freigegebene Dataset verwendet, das nächste Mal öffnet, wird die Datasetabfrage ausgeführt, und der Berichtsserver fügt wieder eine Kopie der aktualisierten Daten in den Cache ein.  
  
 **Cacheablauf nach folgendem Zeitplan**  
 Planen Sie den Zeitraum, nach dem die zwischengespeicherten Daten nicht mehr gültig sind und aus dem Cache entfernt werden. Als Zeitplan kann ein freigegebener Zeitplan oder ein Plan verwendet werden, der nur auf das aktuelle freigegebene Dataset angewendet wird.  
  
 **Datasetspezifischer Zeitplan**  
 Geben Sie einen Zeitplan an, der nur von diesem Dataset verwendet wird.  
  
 **Freigegebenen Zeitplan**  
 Geben Sie einen Zeitplan an, der für Berichte, Abonnements und andere freigegebene Datasets gemeinsam verwendet wird.  
  
 **Anwenden**  
 Speichern Sie die Änderungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Zwischenspeichern von freigegebenen Datasets (SSRS)](report-server/cache-shared-datasets-ssrs.md)   
 [Zeitpläne](subscriptions/schedules.md)  
  
  
