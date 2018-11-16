---
title: Markieren von Geschäftsobjekten als sicher für Skripting | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 729daea7fe719f33ec8931424143c3fedc5ac86f
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558327"
---
# <a name="marking-business-objects-as-safe-for-scripting"></a>Markieren von Geschäftsobjekten als sicher für das Skripting
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Um eine sichere Umgebung für die Internet gewährleisten, müssen Sie Geschäftsobjekte mit instanziiert markieren die [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) des Objekts [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) Methode als "sicher für Skripting". Sie müssen sicherstellen, dass sie als solche gekennzeichnet werden im Bereich "Lizenz" von der Registrierung des Systems, bevor sie in DCOM verwendet werden können.  
  
> [!NOTE]
>  Business-Objekten, die als "sicher für Skripting" oder für die Initialisierung gekennzeichnet können instanziiert und initialisiert von jedem Benutzer, über das Netzwerk. Ein Geschäftsobjekt "sicher für Skripting" markiert ist nicht sicher erleichtern. Es ist äußerst wichtig, um sicherzustellen, dass die Geschäftsobjekte codiert sind, mit der höchsten Sicherheit, um sicherzustellen, dass solche Objekte einen ungeschützten Zugriffspunkt für vertrauliche Daten nicht vorhanden ist.  
  
 Erstellen Sie eine Textdatei mit der Erweiterung REG, die den folgenden Text enthält, um das Geschäftsobjekt als sicher für Skripting manuell zu markieren. In diesem Beispiel \< *MyActiveXGUID*> ist die GUID-Hexadezimalzahl Ihres Business-Objekts. Die folgenden zwei Zahlen wird das sichere Skripting-Feature aktivieren:  
  
```console
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]  
```  
  
 Speichern Sie die Datei, und in der Registrierung durch Verwendung des Registrierungs-Editors oder durch Doppelklicken auf die REG-Datei in Windows Explorer zusammenführen.  
  
 Business-Objekten, die in Microsoft Visual Basic erstellt können mit dem Paket und die Bereitstellungs-Assistent automatisch als "sicher für Skripting" markiert. Wenn Sie angeben, die Sicherheitseinstellungen des Assistenten gefragt werden, wählen Sie **sicher für die Initialisierung** und **sicher für Skripting**.  
  
 Im letzten Schritt wird der Setup-Assistent-Anwendung erstellt, eine htm- und einer CAB-Datei. Sie können diese beiden Dateien auf den Zielcomputer kopieren und doppelklicken Sie auf die HTM-Datei, um die Seite laden und registrieren Sie den Server ordnungsgemäß.  
  
 Da das Geschäftsobjekt, das standardmäßig im Verzeichnis Windows\System32\Occache installiert werden, verschieben Sie es auf das Verzeichnis "Windows\System32", und ändern Sie die **HKEY_CLASSES_ROOT\CLSID\\**  \< *MyActiveXGUID*>\\**InprocServer32** Registrierungsschlüssel mit den richtigen Pfad übereinstimmen.


