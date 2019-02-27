---
title: Identitätswechsel in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 01/21/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 981b98523a53e0c828de5e9cdf8a6c35c6843805
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852905"
---
# <a name="impersonation"></a>Identitätswechsel 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Dieser Artikel enthält die Entwickler von tabellarischen Modellen einen Überblick über die Anmeldeinformationen von Analysis Services Verwendung beim Herstellen einer Verbindung mit einer Datenquelle zum Importieren von Daten und verarbeiten (aktualisieren).  

##  <a name="bkmk_conf_imp_info"></a> Konfigurieren des Identitätswechsels  
 Ein Modell, in dem und in welchem Kontext vorhanden ist wird bestimmt, wie die Identitätswechselinformationen konfiguriert ist. Beim Erstellen eines neuen modellprojekts wird Identitätswechsel beim Herstellen einer Verbindung mit einer Datenquelle zum Importieren von Daten in SQL Server Data Tools (SSDT) konfiguriert. Nachdem ein Modell bereitgestellt wurde, kann Identitätswechsel in Model-Datenbankeigenschaft einer Verbindungszeichenfolge konfiguriert werden, mithilfe von SQL Server Management Studio (SSMS). Für tabellarische Modelle in Azure Analysis Services, verwenden Sie SSMS oder die **anzeigen als: Skript** -Modus im Designer browserbasierte so bearbeiten Sie die Datei "Model.bim" im JSON-Format.
  
##  <a name="bkmk_how_imper"></a> Wie der Identitätswechsel verwendet wird  
 *Identitätswechsel* ist die Fähigkeit einer Serveranwendung, z.B. Analysis Services, die Identität einer Clientanwendung anzunehmen. Analysis Services ausgeführt wird, verwenden eines Dienstkontos, allerdings, wenn der Server eine Verbindung mit einer Datenquelle herstellt Anwendung ein Identitätswechsel verwendet, damit für den Datenimport und die Verarbeitung zugriffsüberprüfungen kann ausgeführt werden.  
  
 Für den Identitätswechsel verwendete Anmeldeinformationen unterscheiden sich von den Anmeldeinformationen, die, denen Sie gerade auf mit angemeldet sind. Melden Sie sich die Anmeldeinformationen des Benutzers dienen für bestimmte clientseitige Vorgänge beim Erstellen eines Modells.  
  
 Es ist wichtig um zu verstehen, wie Identitätswechsel-Anmeldeinformationen angegeben sind und geschützt, sowie den Unterschied zwischen den Kontexten, in die beiden Ihrem angemeldeten auf Benutzeranmeldeinformationen verwendet werden, und wenn andere Identitätswechsel-Anmeldeinformationen verwendet werden.  
  
 **Grundlegendes zu serverseitigen Anmeldeinformationen**  
 
Wenn Daten nicht importiert oder verarbeitet werden, werden Identitätswechsel-Anmeldeinformationen verwendet, um Verbindungen mit der Datenquelle herstellen und die Daten abzurufen. Diese Verbindung ist ein *serverseitige* Vorgang im Kontext einer Clientanwendung ausgeführt werden, da Analysis Services-Server, die arbeitsbereichsdatenbank hostet, eine Verbindung mit der Datenquelle her, und die Daten abruft.  
  
 Wenn Sie ein Modell auf einem Analysis Services-Server bereitstellen und sich die Arbeitsbereichsdatenbank während der Bereitstellung des Modells im Arbeitsspeicher befindet, werden die Anmeldeinformationen an den Analysis Services-Server übergeben, auf dem das Modell bereitgestellt wird. Benutzeranmeldeinformationen sind nicht auf dem Datenträger gespeichert.  
  
 Wenn ein bereitgestelltes Modell die Daten aus einer Datenquelle verarbeitet, werden die Identitätswechselinformationen, die in der Datenbank im Arbeitsspeicher beibehalten verwendet, um Verbindungen mit der Datenquelle herstellen und die Daten abzurufen. Da dieser Vorgang durch den Analysis Services-Server, der die Modelldatenbank verwaltet wird, ist die Verbindung erneut einen serverseitigen Vorgang.  
  
 **Grundlegendes zu clientseitigen Anmeldeinformationen**  
  
 Wenn ein neues Modell erstellen oder eine Datenquelle zu einem vorhandenen Modell hinzufügen, Sie eine Verbindung mit einer Datenquelle herstellen und Tabellen und Sichten in das Modell importiert werden sollen. In den Tabellenimport-Assistenten oder Abrufen von Data\Query-Designer-Vorschau und Filter-Funktionen sehen Sie ein Beispiel für die zu importierenden Daten. Sie können auch angeben, dass Filter, um Daten auszuschließen, die im Modell nicht benötigt.  
  
 Auf ähnliche Weise für vorhandene Modelle, die bereits erstellt wurden, verwenden Sie die **Tabelleneigenschaften** Dialogfeld, um die Vorschau und Filtern von Daten in eine Tabelle importiert.  
  
 Die Vorschau und Filter-Funktionen, **Tabelleneigenschaften**, und **Partitions-Manager** Dialogfelder sind einen in-Process *clientseitige* Vorgang; das heißt, was während dieser ausgeführt wird Vorgang unterscheiden sich wie mit die Datenquelle verbunden ist, und Daten aus der Datenquelle abgerufen; einen serverseitigen Vorgang. Die Vorschau und Filtern von Daten verwendeten Anmeldeinformationen sind die Anmeldeinformationen des aktuell angemeldeten Benutzers. In der Tat, Ihre Anmeldeinformationen. 
  
 Die Trennung von Anmeldeinformationen verwendet, bei der serverseitigen, und clientseitigen Vorgängen können, einen Konflikt zwischen in was Sie sehen, und welche Daten abgerufen werden, während eines Imports oder der Prozess (serverseitige Vorgänge) führen. Wenn die Anmeldeinformationen für Sie angemeldet sind und unterscheiden sich die angegebenen Identitätswechselinformationen, die Daten sehen Sie in der Vorschau und Filter-Funktionen oder die **Tabelleneigenschaften** Dialogfeld, und die Daten abgerufen werden, während eines Imports oder Prozess kann variieren, je nachdem die Anmeldeinformationen, die von der Datenquelle erforderlich sein.  
  
> [!IMPORTANT]  
>  Bei der Modellerstellung, stellen Sie die Anmeldeinformationen, die mit dem Sie angemeldet sind, und die für einen Identitätswechsel angegebenen Anmeldeinformationen über ausreichende Berechtigungen zum Abrufen der Daten aus der Datenquelle verfügen.
  
##  <a name="bkmk_imp_info_options"></a> enthalten  
 Wenn Identitätswechsel konfigurieren oder Eigenschaften für eine vorhandene Datasource-Verbindung bearbeiten, geben Sie eine der folgenden Optionen aus:  
  
**Tabellarischen Modellen für Kompatibilitätsgrad 1400 und höher**
 
|Option|Description|  
|------------|-----------------|  
|**Identität des Kontos annehmen**|Gibt an, das Modell ein Windows-Benutzerkonto zum Importieren oder Verarbeiten von Daten aus der Datenquelle. Die Domäne und den Namen des Benutzerkontos folgen dem folgenden Format:**\<Domänenname >\\< Benutzerkontoname\>**.|  
|**Identität des aktuellen Benutzers**|Gibt an, dass die Daten zugegriffen werden soll, aus der Datenquelle, die mit der Identität des Benutzers, der die Anforderung gesendet wird. Diese Einstellung gilt nur für DirectQuery-Modus.|  
|**Identität annehmen**|Gibt den Benutzernamen für den Zugriff auf die Datenquelle, jedoch nicht das Kennwort des Kontos angeben müssen. Diese Einstellung gilt nur, wenn die Kerberos-Delegierung aktiviert ist, und gibt an, dass die S4U-Authentifizierung verwendet werden soll.|  
|**Identität des Dienstkontos annehmen**|Gibt an, das Modell die Sicherheitsanmeldeinformationen, die das Objekt verwaltet, die Analysis Services-Dienstinstanz zugeordnet.|  
|**Identität des unbeaufsichtigten Kontos annehmen**|Gibt an, die Analysis Services-Engine des ein vorkonfiguriert, dass für die unbeaufsichtigte Konto für den Datenzugriff verwendet werden soll.|  

> [!IMPORTANT]
> Identität Aktueller Benutzer wird in einigen Umgebungen nicht unterstützt. Identität Aktueller Benutzer wird für Azure Analysis Services, die mit lokalen Datenquellen verbunden bereitgestellten tabellarischen Modellen nicht unterstützt. Da eine Azure Analysis Services-Server-Ressource nicht in einer Organisation Domäne verbunden ist, können keine Clientanmeldeinformationen für einen Data Source Server in der Domäne authentifiziert werden. Azure Analysis Services kann auch nicht derzeit mit SQL-Datenbank (Azure)-Unterstützung für einmaliges Anmelden (SSO) integriert werden. Abhängig von Ihrer Umgebung haben andere identitätswechseleinstellungen auch Einschränkungen auf. Beim Versuch, eine identitätswechseleinstellung zu verwenden, die nicht unterstützt wird, wird ein Fehler zurückgegeben. 


**Tabellarische 1200-Modelle**
 
|Option|Description|  
|------------|-----------------|  
|**Bestimmten Windows-Benutzernamen und Kennwort**|Diese Option gibt an das Modell ein Windows-Benutzerkonto zum Importieren oder Verarbeiten von Daten aus der Datenquelle. Die Domäne und den Namen des Benutzerkontos folgen dem folgenden Format:**\<Domänenname >\\< Benutzerkontoname\>**. Wenn Sie ein neues Modell mit dem Tabellenimport-Assistenten erstellen, ist diese Einstellung die Standardoption.|  
|**Dienstkonto**|Diese Option gibt an, dass das Modell die Sicherheitsanmeldeinformationen verwendet, die der Analysis Services-Dienstinstanz zugeordnet sind, die das Modell verwaltet.|  
  
##  <a name="bkmk_impers_sec"></a> Sicherheit  
 Für den Identitätswechsel verwendete Anmeldeinformationen sind dauerhaft im Arbeitsspeicher von der VertiPaq™-Engine. Anmeldeinformationen wurden nicht auf dem Datenträger. Wenn die arbeitsbereichsdatenbank nicht im Arbeitsspeicher ist, wenn das Modell bereitgestellt wird, wird der Benutzer aufgefordert, die Anmeldeinformationen zur Verbindung mit der Datenquelle und Abrufen der Daten einzugeben.  
  
> [!NOTE]  
>  Es wird empfohlen, ein Windows-Benutzerkonto und ein Kennwort für die Identitätswechselinformationen anzugeben. Ein Windows-Benutzerkonto kann für die mindestens erforderlichen Berechtigungen zum Herstellen einer Verbindung mit und zum Lesen von Daten aus der Datenquelle konfiguriert werden.  
  

  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Bereitstellung von Tabellenmodelllösungen](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
