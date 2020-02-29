---
title: Verwenden einer Notification-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177000"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Verwenden einer Notification-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse befindet sich im <xref:Microsoft.ReportingServices.Interfaces>-Namespace und stellt Abonnementdaten dar, die die Übermittlungserweiterungen für die Übermittlung von Berichten verwenden. Die <xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse verfügt über mehrere Eigenschaften, die verwendet werden können, um die Berichte für die Übermittlung zu rendern, den Status der Benachrichtigung zu bestimmen und die Benutzerdaten festzulegen.

 ![Berichts Benachrichtigungs Prozess](../../media/bk-ext-03.gif "Berichtsbenachrichtigungsprozess") Die Benachrichtigung ist das zentrale Objekt einer beliebigen Übermittlung.

 Wenn ein Ereignis eintritt, das zu einem Abonnement gehört, das Ihre benutzerdefinierte Übermittlungserweiterung verwendet, wird eine Benachrichtigung mit einem <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt erstellt. Das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt umfasst Funktionen, die benötigt werden, um einen bestimmten Bericht in einem unterstützten Renderingformat zu rendern, und enthält berichtsspezifische Eigenschaften, wie die URL zum Bericht auf dem Server und den Namen des Berichts. Weitere Informationen zur <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse finden Sie unter [Verwenden der Report-Klasse für eine Übermittlungserweiterung](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).

 Sie übergeben das <xref:Microsoft.ReportingServices.Interfaces.Notification>-Objekt an die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode Ihrer Übermittlungserweiterung. Die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode sollte speziellen Code zur Verarbeitung der Benachrichtigung und zur Übermittlung des Berichts enthalten.

 Ein Beispiel für die Verwendung der <xref:Microsoft.ReportingServices.Interfaces.Notification> -Klasse finden Sie unter [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).

## <a name="retry-functionality"></a>Funktion zum Wiederholen
 Mit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Sie für Benachrichtigungen, die nicht sofort übermittelt werden können, eine Wiederholungswarteschlange erstellen. Nachdem der Berichtsserver die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode einer Übermittlungserweiterung aufruft, kann die Übermittlungserweiterung anfordern, dass der Berichtsserver die Übermittlung zu einem späteren Zeitpunkt wiederholt. In diesem Fall stellt der Berichtsserver die Benachrichtigung in eine interne Warteschlange und wiederholt die Übermittlung nach einem bestimmten Zeitraum. Administratoren können die maximale Anzahl von Wiederholungsversuchen, die der Berichtsserver ausführen soll, und den Zeitraum zwischen den Wiederholungen im Bereich der Übermittlungserweiterung der Datei „RSReportServer.config“ konfigurieren. Dazu verwenden sie die XML-Elemente **MaxNumberOfRetries** und **PeriodBetweenRetries**. Benachrichtigungen werden aus der Wiederholungswarteschlange entfernt, wenn die Übermittlung später erfolgreich oder die maximale Anzahl an Wiederholungsversuchen erreicht ist. Wenn die Übermittlung nach der maximalen Anzahl von Wiederholungen fehlschlägt, wird die Benachrichtigung entfernt.

## <a name="see-also"></a>Weitere Informationen
 [Implementieren einer Übermittlungs Erweiterung](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services Erweiterungs Bibliothek](../reporting-services-extension-library.md)


