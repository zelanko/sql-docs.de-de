---
title: Berichtsserver-Elementeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- item-specific properties [Reporting Services]
- report items [Reporting Services], properties
- items [Reporting Services], properties
ms.assetid: 21edec6d-9897-48fb-8c75-182305b1dbdb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ed8a56892cfd70b43341ffff8349faa56094a97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62519140"
---
# <a name="report-server-item-properties"></a>Eigenschaften der Berichtsserverelemente
  Elementeigenschaften sind Eigenschaften, die für Elemente in der Berichtsserver-Datenbank spezifisch sind. Zu diesen Elementen gehören Berichte, verlinkte Berichte, Ordner, Ressourcen, Modelle und Datenquellen.  
  
 Folgende Namen der Elementeigenschaften sind reserviert. Sie können keine benutzerdefinierten Eigenschaften des gleichen Namens erstellen. Sie können viele dieser Eigenschaften mit den Webdienstmethoden für Berichtsserver lesen oder ändern.  
  
## <a name="item-properties"></a>Elementeigenschaften  
 Folgende Eigenschaften gelten für alle Elemente in der Berichtsserver-Datenbank.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**CreatedBy**|Der Name des Benutzers, der das Element ursprünglich zur Berichtsserver-Datenbank hinzugefügt hat.|  
|**CreationDate**|Der Zeitpunkt (Datum und Uhrzeit), zu dem das Element zur Berichtsserver-Datenbank hinzugefügt wurde.|  
|**Beschreibung**|Die Beschreibung des Elements.|  
|**Hidden**|Ein Wert, der angibt, ob das Element für Benutzer sichtbar und verfügbar ist.|  
|**ID**|Die ID eines Elements in der Berichtsserver-Datenbank.|  
|**ModifiedBy**|Der Name des Benutzers, der das Element als Letzter in der Berichtsserver-Datenbank geändert hat.|  
|**ModifiedDate**|Zeitpunkt (Datum und Uhrzeit) der letzten Änderung des Elements durch den Benutzer.|  
|**Name**|Der Name eines Elements in der Berichtsserver-Datenbank.|  
|**Pfad**|Der vollständige Pfadname des Elements. Der Pfad jedes Elements in der Berichtsserver-Datenbank hat eine maximale Zeichenlänge von 260.|  
|**Größe**|Die Größe eines Elements (in Byte) in der Berichtsserver-Datenbank.|  
|**Typ**|Der Typ eines Elements in der Berichtsserver-Datenbank.|  
|**VirtualPath**|Der virtuelle Pfad zu einem Element in der Berichtsserver-Datenbank. Der Wert der <xref:ReportService2010.CatalogItem.VirtualPath%2A>-Eigenschaft ist der Pfad, in dem der Benutzer das Element findet. Ein Bericht mit dem Namen report1, der sich im persönlichen Ordner des Benutzers "Meine Berichte" befindet, hat den virtuellen Pfad /My Reports. Der tatsächliche Pfad des Elements ist /Benutzer /Benutzername /Meine Berichte.|  
  
## <a name="folder-properties"></a>Ordnereigenschaften  
 Zusätzlich zu den zuvor aufgeführten Elementeigenschaften gilt folgende Eigenschaft für Ordner in der Berichtsserver-Datenbank.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**Reserved**|Ein Wert, der von der <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode für Ordner zurückgegeben wurde, die vom Berichtsserver reserviert sind. Reservierte Ordner enthalten Benutzer, Meine Berichte und /. Reservierte Ordner können nicht geändert oder entfernt werden.|  
  
## <a name="report-properties"></a>Berichtseigenschaften  
 Zusätzlich zu den zuvor aufgeführten Elementeigenschaften gelten folgende Eigenschaften für Berichte in der Berichtsserver-Datenbank.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**Sprache**|Die in einem Bericht verwendete Sprache. Der Wert ist ein Sprachcode, der in der IETF-Spezifikation (Internet Engineering Task Force) RFC1766 definiert ist. Der erste Teil ist eine Bezeichnung aus zwei Zeichen für die Basissprache. Der zweite Teil ist durch einen Bindestrich getrennt und legt die Variation oder den Dialekt der Sprache fest. Wenn der Wert nicht im `Style`-Element angegeben ist, das zum `Body`-Element in der Berichtsdefinition gehört, entspricht der Standardwert der Sprache des Berichtsservers.|  
|`ReportProcessingTimeout`|Timeout (in Sekunden) für einen einzelnen Bericht. Wenn dieser Wert festgelegt ist, versucht der Berichtsserver, die Verarbeitung eines Berichts zu beenden, sobald der angegebene Zeitraum überschritten wird. Gültige Werte sind `-1` und `2`,`147`,`483`,`647`. Wenn der Wert `-1` ist, findet bei Berichten während der Verarbeitung kein Timeout statt. Wenn der Wert ist `null`, den Wert der Systemeigenschaft `ReportProcessingTimeout` wird für die berichtsverarbeitungstimeout verwendet. Der Standardwert ist `null`. Weitere Informationen finden Sie unter [Berichtsserver-Systemeigenschaften](reporting-services-properties-report-server-system-properties.md).|  
|**ExecutionDate**|Zeitpunkt (Datum und Uhrzeit), zu dem zuletzt eine Berichtsmomentaufnahme für einen Bericht erstellt wurde.|  
|**CanRunUnattended**|Ein Wert, der angibt, ob ein Bericht unbeaufsichtigt nach einem Zeitplan ausgeführt werden kann. Ist diese Eigenschaft auf `true` eingestellt, sind die Standardwerte für die Berichtsparameter definiert, und die Anmeldeinformationen für die Datenquelle werden mit dem Bericht gespeichert, oder die Option zum Abrufen der Anmeldeinformationen ist auf `None` eingestellt. Ist diese Eigenschaft auf `false` eingestellt, sind die Voraussetzungen zum unbeaufsichtigten Ausführen eines Berichts nicht erfüllt. Weitere Informationen finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
|**HasParameterDefaultValues**|Ein Wert, der angibt, ob im Bericht gültige Standardwerte für alle Berichtsparameter festgelegt wurden. Der Wert lautet auch `true`, wenn ein Bericht keine Berichtsparameter hat. Wenn diese Eigenschaft `false` lautet, verfügen ein oder mehrere Berichtsparameter über keinen gültigen Standardwert.|  
|**HasDataSourceCredentials**|Ein Wert, der angibt, dass die Option zum Abrufen der Anmeldeinformationen für alle zum Bericht gehörigen Datenquellen entweder `None` oder `Store` lautet. Wenn diese Eigenschaft `false` lautet, ist eine Option zum Abrufen der Anmeldeinformationen für eine der zum Bericht gehörigen Datenquellen auf `Integrated` oder auf `Prompt` eingestellt.|  
|**IsSnapshotExecution**|Ein Wert, der angibt, ob der Bericht eine Momentaufnahme ist.|  
|**HasScheduleReadyDataSources**|Ein Wert, der angibt, ob die Datenquellen eines Berichts so konfiguriert sind, dass die geplante Ausführung unterstützt wird. Wenn die Eigenschaft auf `false` eingestellt ist, können die Benutzer den Bericht nicht abonnieren.|  
  
## <a name="resource-properties"></a>Ressourceneigenschaften  
 Zusätzlich zu den zuvor aufgeführten Elementeigenschaften gilt folgende Eigenschaft für Ressourcen in der Berichtsserver-Datenbank.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|**MimeType**|Der MIME-Typ einer Ressource in der Berichtsserver-Datenbank.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  
