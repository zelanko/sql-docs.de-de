---
title: Markieren von Geschäftsobjekten als sicher für die Skripterstellung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 0be98d1a-ab3d-4dce-a166-dacda10d154a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55ae560f35a06e77803bfb011f4d430d5079ea05
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922605"
---
# <a name="marking-business-objects-as-safe-for-scripting"></a>Markieren von Geschäftsobjekten als sicher für das Skripting
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Um eine sichere Internet Umgebung zu gewährleisten, müssen Sie alle Geschäftsobjekte markieren, die mit dem RDS-Objekt instanziiert werden [. ](../../../ado/reference/rds-api/dataspace-object-rds.md)Die Methode " [kreateobject](../../../ado/reference/rds-api/createobject-method-rds.md) " des DataSpace-Objekts als "sicher für Skripting". Sie müssen sicherstellen, dass Sie im Lizenzbereich der Systemregistrierung als solche gekennzeichnet sind, bevor Sie in DCOM verwendet werden können.  
  
> [!NOTE]
>  Geschäftsobjekte, die als "sicher für Skripting" oder sicher für die Initialisierung gekennzeichnet sind, können von allen Benutzern über das Netzwerk instanziiert und initialisiert werden. Wenn Sie ein Geschäftsobjekt "sicher für Skripting" markieren, ist es nicht sicher. Es ist von entscheidender Bedeutung, sicherzustellen, dass Geschäftsobjekte mit der höchsten Sicherheit codiert werden, um sicherzustellen, dass solche Objekte keinen ungeschützten Zugriffspunkt für sensible Daten darstellen.  
  
 Um das Geschäftsobjekt manuell als sicher für die Skripterstellung zu markieren, erstellen Sie eine Textdatei mit der Erweiterung. reg, die den folgenden Text enthält. In diesem Beispiel \<ist *myactivexguid*> die hexadezimale GUID-Nummer Ihres Geschäftsobjekts. Die folgenden beiden Zahlen aktivieren das Feature für die sichere Skripterstellung:  
  
```console
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]  
```  
  
 Speichern Sie die Datei, und führen Sie Sie mithilfe des Registrierungs-Editors in die Registrierung zusammen, oder Doppelklicken Sie im Windows-Explorer auf die reg-Datei.  
  
 Geschäftsobjekte, die in Microsoft Visual Basic erstellt werden, können mit dem Paket-und Bereitstellungs-Assistenten automatisch als "sicher für Skripting" gekennzeichnet werden. Wenn Sie vom Assistenten aufgefordert werden, Sicherheitseinstellungen anzugeben, wählen Sie **sicher für Initialisierung** und **sicher für Skripterstellung aus**.  
  
 Im letzten Schritt erstellt der Anwendungssetup-Assistent eine htm-und eine CAB-Datei. Anschließend können Sie diese beiden Dateien auf den Zielcomputer kopieren und auf die HTM-Datei doppelklicken, um die Seite zu laden und den Server ordnungsgemäß zu registrieren.  
  
 Da das Geschäftsobjekt standardmäßig im Verzeichnis Windows\System32\Occache installiert wird, verschieben Sie es in das Verzeichnis Windows\System32, und ändern Sie den Registrierungsschlüssel **HKEY_CLASSES_ROOT\\\CLSID**\<*myactivexguid*>\\**InProcServer32** so, dass er dem richtigen Pfad entspricht.


