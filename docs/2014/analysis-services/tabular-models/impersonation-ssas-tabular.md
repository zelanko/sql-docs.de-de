---
title: Identitätswechsel (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fcc79e96-182a-45e9-8ae2-aeb440e9bedd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81e8f9ae90db3c7613ccb99039d70d9a28c5a113
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067062"
---
# <a name="impersonation-ssas-tabular"></a>Identitätswechsel (SSAS – tabellarisch)
  Dieses Thema vermittelt Autoren von tabellarischen Modellen Grundlegendes zur Verwendung von Anmeldedaten durch Analysis Services beim Herstellen einer Verbindung mit einer Datenquelle zum Importieren und Verarbeiten (Aktualisieren) von Daten.  
  
 Dieser Artikel enthält folgende Abschnitte:  
  
-   [Vorteile](#bkmk_how_imper)  
  
-   [Optionen](#bkmk_imp_info_options)  
  
-   [Sicherheit](#bkmk_impers_sec)  
  
-   [Identitätswechsel beim Importieren eines Modells](#bkmk_imp_newmodel)  
  
-   [Konfigurieren des Identitäts Wechsels](#bkmk_conf_imp_info)  
  
##  <a name="bkmk_how_imper"></a> Vorteile  
 Identitäts *Wechsel ist die* Fähigkeit einer Serveranwendung, wie z. b. Analysis Services, die Identität einer Client Anwendung anzunehmen. Analysis Services wird über ein Dienstkonto ausgeführt. Wenn der Server jedoch eine Verbindung zu einer Datenquelle herstellt, wird für die Anwendung ein Identitätswechsel verwendet, sodass für den Datenimport und die Verarbeitung Zugriffsüberprüfungen ausgeführt werden können.  
  
 Die für den Identitätswechsel verwendeten Anmeldeinformationen unterscheiden sich von den Anmeldeinformationen des gerade angemeldeten Benutzers. Die Anmeldeinformationen des angemeldeten Benutzers werden für bestimmte clientseitige Vorgänge beim Erstellen eines Modells verwendet.  
  
 Es ist wichtig zu verstehen, wie Identitätswechsel-Anmelde Informationen angegeben und gesichert werden, sowie den Unterschied zwischen Kontexten, in denen sowohl die Anmelde Informationen des aktuellen angemeldeten Benutzers als auch andere Anmelde Informationen verwendet werden.  
  
 **Grundlegendes zu serverseitigen Anmelde Informationen**  
  
 In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]werden Anmeldeinformationen für jede Datenquelle im Tabellenimport-Assistenten auf der Seite **Identitätswechselinformationen** oder durch Bearbeitung einer vorhandenen Datenquellenverbindung im Dialogfeld **Vorhandene Verbindungen** angegeben.  
  
 Beim Importieren oder Verarbeiten von Daten werden die auf der Seite **Identitätswechselinformationen** angegebenen Anmeldeinformationen verwendet, um eine Verbindung mit der Datenquelle herzustellen und die Daten abzurufen. Dabei handelt es sich um einen *serverseitigen* Vorgang, der im Kontext einer Clientanwendung ausgeführt wird, da der Analysis Services-Server, der die Arbeitsbereichsdatenbank hostet, eine Verbindung mit der Datenquelle herstellt und die Daten abruft.  
  
 Wenn Sie ein Modell auf einem Analysis Services-Server bereitstellen und sich die Arbeitsbereichsdatenbank während der Bereitstellung des Modells im Arbeitsspeicher befindet, werden die Anmeldeinformationen an den Analysis Services-Server übergeben, auf dem das Modell bereitgestellt wird. Zu keinem Zeitpunkt werden Benutzeranmeldeinformationen auf dem Datenträger gespeichert.  
  
 Wenn ein bereitgestelltes Modell die Daten aus einer Datenquelle verarbeitet, werden die in der speicherinternen Datenbank dauerhaft gespeicherten Identitätswechselinformationen verwendet, um eine Verbindung mit der Datenquelle herzustellen und die Daten abzurufen. Da dieser Prozess vom Analysis Services-Server, der die Modelldatenbank verwaltet, durchgeführt wird, handelt es sich auch hierbei um einen serverseitigen Vorgang.  
  
 **Grundlegendes zu Client seitigen Anmelde Informationen**  
  
 Wenn Sie ein neues Modell erstellen oder eine Datenquelle zu einem vorhandenen Modell hinzufügen, verwenden Sie den Tabellenimport-Assistenten, um eine Verbindung mit einer Datenquelle herzustellen und Tabellen und Sichten für den Import in das Modell auszuwählen. Sie können im Tabellenimport-Assistenten auf der Seite **Tabellen und Sichten auswählen** die Funktion **Vorschau und Filter** verwenden, um ein Beispiel (maximal 50 Zeilen) der zu importierenden Daten anzuzeigen. Sie können auch Filter angeben, um Daten auszuschließen, die im Modell nicht erforderlich sind.  
  
 Auf ähnliche Weise können Sie für bereits erstellte Modelle das Dialogfeld **Tabelleneigenschaften bearbeiten** verwenden, um in eine Tabelle importierte Daten anzuzeigen und zu filtern. Diese Vorschau- und Filterfunktionen werden genauso verwendet wie die Funktion **Vorschau und Filter** auf der Seite **Tabellen und Sichten auswählen** des Tabellenimport-Assistenten.  
  
 Bei der Funktion **Vorschau und Filter** sowie den Dialogfeldern **Tabelleneigenschaften** und **Partitions-Manager** handelt es sich um prozessinterne *clientseitige* Vorgänge. Dies bedeutet, dass diese Vorgänge anders durchgeführt werden als die serverseitigen Vorgänge, bei denen die Datenquelle verbunden und Daten aus der Datenquelle abgerufen werden. Die Anmeldeinformationen, die zum Anzeigen einer Vorschau und Filtern der Daten verwendet werden, sind die Anmeldeinformationen des Benutzers, der zu dem Zeitpunkt angemeldet ist. Client seitige Vorgänge verwenden immer die Windows-Anmelde Informationen des aktuellen Benutzers, um eine Verbindung mit der Datenquelle herzustellen.  
  
 Die unterschiedliche Verwendung der Anmeldeinformationen bei serverseitigen und clientseitigen Vorgängen kann dazu führen, dass die Daten, die der Benutzer bei Verwendung der Funktion **Vorschau und Filter** oder des Dialogfelds **Tabelleneigenschaften** (clientseitige Vorgänge) sieht, nicht mit den Daten übereinstimmen, die während eines Imports oder einer Verarbeitung abgerufen werden (serverseitige Vorgänge). Wenn die Anmeldeinformationen des gerade angemeldeten Benutzers und die angegebenen Identitätswechselinformationen unterschiedlich sind, können sich die mit der Funktion **Vorschau und Filter** oder dem Dialogfeld **Tabelleneigenschaften** angezeigten und die während eines Imports oder einer Verarbeitung abgerufenen Daten abhängig davon, welche Anmeldeinformationen die Datenquelle erfordert, unterscheiden.  
  
> [!IMPORTANT]  
>  Wenn Sie ein Modell erstellen, stellen Sie sicher, dass die Anmeldeinformationen des gerade angemeldeten Benutzers und die für einen Identitätswechsel angegebenen Anmeldeinformationen über ausreichende Rechte verfügen, um die Daten von der Datenquelle abzurufen.  
  
##  <a name="bkmk_imp_info_options"></a>Optionen  
 Wenn Sie den Identitätswechsel konfigurieren oder Eigenschaften für eine vorhandene Datenquellenverbindung in Analysis Services bearbeiten, können Sie eine der folgenden Optionen angeben:  
  
|Option|Identitätswechsel Modus<sup>1</sup>|BESCHREIBUNG|  
|------------|-----------------------------------|-----------------|  
|**Bestimmter Windows-Benutzername und Kennwort** <sup>2</sup>|ImpersonateWindowsUserAccount|Diese Option gibt an, dass das Modell ein Windows-Benutzerkonto verwendet, um Daten aus der Datenquelle zu importieren oder zu verarbeiten. Die Domäne und der Name des Benutzerkontos verwenden das folgende Format:**\<Domänen Name \\><Benutzerkonto\>Name**. Beim Erstellen eines neuen Modells mit dem Tabellenimport-Assistenten ist dies die Standardoption.|  
|**Dienst Konto**|ImpersonateServiceAccount|Diese Option gibt an, dass das Modell die Sicherheitsanmeldeinformationen verwendet, die der Analysis Services-Dienstinstanz zugeordnet sind, die das Modell verwaltet.|  
  
 <sup>1</sup> Identitätswechsel Modus gibt den Wert für das [DataSourceImpersonationInfo-Element &#40;ASSL-&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) Eigenschaft in der Datenquelle an.  
  
 <sup>2</sup> Wenn Sie diese Option verwenden, wenn die Arbeitsbereichs Datenbank aus dem Arbeitsspeicher entfernt wird, entweder aufgrund eines Neustarts oder wenn die Eigenschaft **Arbeitsbereichs Beibehaltung** auf aus dem Arbeits **Speicher entladen** oder **aus dem Arbeitsbereich löschen**festgelegt ist, und das Modellprojekt geschlossen wird, werden Sie in der nachfolgenden Sitzung aufgefordert, die Anmelde Informationen für jede Datenquelle einzugeben. Analog dazu werden Sie aufgefordert, die Anmeldeinformationen für jede Datenquelle einzugeben, wenn eine bereitgestellte Modelldatenbank aus dem Arbeitsspeicher entfernt wird.  
  
##  <a name="bkmk_impers_sec"></a> Sicherheit  
 Die für den Identitätswechsel verwendeten Informationen werden von der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq)™ dauerhaft im Arbeitsspeicher gespeichert, das dem Analysis Services-Server zugeordnet ist, der die Arbeitsbereichsdatenbank oder eine bereitgestellte Modelldatenbank verwaltet.  Anmeldeinformationen werden zu keinem Zeitpunkt auf den Datenträger geschrieben. Wenn sich die Datenbank des Arbeitsbereichs bei der Bereitstellung des Modells nicht im Arbeitsspeicher befindet, wird der Benutzer aufgefordert, die Anmeldeinformationen einzugeben, die zum Herstellen einer Verbindung mit der Datenquelle und Abrufen der Daten verwendet werden.  
  
> [!NOTE]  
>  Es wird empfohlen, ein Windows-Benutzerkonto und ein Kennwort für die Identitätswechselinformationen anzugeben. Ein Windows-Benutzerkonto kann so konfiguriert werden, dass die mindestens erforderlichen Berechtigungen zum Herstellen einer Verbindung und Lesen von Daten aus der Datenquelle verwendet werden.  
  
##  <a name="bkmk_imp_newmodel"></a>Identitätswechsel beim Importieren eines Modells  
 Im Gegensatz zu tabellarischen Modellen, die mehrere verschiedene Identitätswechselmodi zur Unterstützung der prozessexternen Datensammlung verwenden können, verwendet PowerPivot nur einen Modus: ImpersonateCurrentUser. Da PowerPivot immer prozessintern ausgeführt wird, wird die Verbindung zu Datenquellen mit den Anmeldeinformationen des gerade angemeldeten Benutzers hergestellt. Bei tabellarischen Modellen werden die Anmeldeinformationen des derzeit angemeldeten Benutzers im Tabellenimport-Assistenten nur mit der Funktion **Vorschau und Filter** und beim Anzeigen der **Tabelleneigenschaften**verwendet. Identitätswechselinformationen werden verwendet, wenn Daten in die Arbeitsbereichsdatenbank oder in ein bereitgestelltes Modell importiert oder darin verarbeitet werden.  
  
 Wenn Sie ein neues Modell erstellen, indem Sie eine vorhandene PowerPivot-Arbeitsmappe importieren, werden die Identitätswechselinformationen vom Modell-Designer standardmäßig für die Verwendung des Dienstkontos konfiguriert (ImpersonateServiceAccount). Es wird empfohlen, die Identitätswechselinformationen für Modelle, die aus PowerPivot importiert wurden, in ein Windows-Benutzerkonto zu ändern. Nachdem die Power Pivot-Arbeitsmappe importiert wurde und das neue Modell im Modell-Designer erstellt wurde, können Sie die Anmelde Informationen über das Dialogfeld **vorhandene Verbindungen** ändern.  
  
 Wenn Sie ein neues Modell erstellen, indem Sie die Daten aus einem vorhandenen Modell auf einem Analysis Services-Server importieren, werden die Identitätswechselinformationen aus der vorhandenen Modelldatenbank in die Arbeitsbereichsdatenbank des neuen Modells übergeben. Sie können die Anmeldeinformationen für das neue Modell ggf. über das Dialogfeld **Vorhandene Verbindungen** ändern.  
  
##  <a name="bkmk_conf_imp_info"></a>Konfigurieren des Identitäts Wechsels  
 Der Speicherort und der Kontext, an dem bzw. in dem sich das Modell befindet, bestimmen die Konfiguration der Identitätswechselinformationen. Für Modelle, die in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erstellt werden, können Sie Identitätswechselinformationen im Tabellenimport-Assistenten auf der Seite **Identitätswechselinformationen** konfigurieren, oder indem Sie die Datenquellenverbindung im Dialogfeld **Vorhandene Verbindungen** bearbeiten. Um vorhandene Verbindungen anzuzeigen, klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]im Menü **Modell** auf **Vorhandene Verbindungen**.  
  
 Für Modelle, die auf einem Analysis Services Server bereitgestellt werden, können Identitätswechsel Informationen konfiguriert werden, indem Sie im Dialogfeld Daten **Bank Eigenschaften** von auf die Schaltfläche mit den Auslassungs Punkten (... [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) der Eigenschaft Identitätswechsel **Informationen der Datenquelle** klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Directquery-Modus &#40;tabellarischen SSAS-&#41;](directquery-mode-ssas-tabular.md)   
 [Datenquellen &#40;tabellarischen SSAS-&#41;](../data-sources-ssas-tabular.md)   
 [Bereitstellung von Tabellen Modelllösungen &#40;tabellarischen SSAS-&#41;](tabular-model-solution-deployment-ssas-tabular.md)  
  
  
