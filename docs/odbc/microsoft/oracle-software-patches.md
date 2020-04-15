---
title: Oracle Software-Patches | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1fb577e7b08f6ef332ed35f6d275a5f7ce543ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292950"
---
# <a name="oracle-software-patches"></a>Oracle-Software-Patches
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Patches für die Oracle-Serverprodukte und deren Clientkomponente sind für das ordnungsgemäße Funktionieren mehrerer Microsoft-Produkte und -Technologien erforderlich, einschließlich des Microsoft ODBC-Treibers für Oracle, des Microsoft OLE DB-Anbieters für Oracle, Internet Information Services (IIS), Component Services (oder Microsoft Transaction Server, wenn Sie Windows NT verwenden) usw.  
  
> [!NOTE]  
>  Die folgenden Anweisungen sind möglicherweise nicht vollständig korrekt, da sich die Oracle FTP-Site ändern kann.  
  
### <a name="to-download-the-oracle-software-patches"></a>So laden Sie die Oracle-Software-Patches herunter  
  
1.  Stellen Sie eine Verbindung mit der öffentlichen FTP-Site auf oracle-ftp.oracle.com her. Die Benutzer-ID ist "anonym" und das Kennwort ist Ihre E-Mail-Adresse.  
  
2.  Navigieren Sie zum folgenden Verzeichnis: /server/wgt_tech/server/windowsNT.  
  
3.  Um Patches herunterzuladen, die für Windows 95, Windows 98 und Windows NT/Windows 2000 am relevantesten sind, navigieren Sie zum Unterverzeichnis für Ihre Version von Oracle - 7.3 oder 8.0. Die beiden Unterverzeichnisse sind /73patchsets und /80patchsets.  
  
4.  Um Patches für die Netzwerktechnologie von Oracle herunterzuladen, entweder SQL*Net oder Net8, navigieren Sie zu folgendem Verzeichnis: /network.  
  
 Der Zugriff auf diese FTP-Site über Ihren Webbrowser funktioniert möglicherweise nicht. Wenn Probleme auftreten, verwenden Sie einen "traditionellen" FTP-Client oder verwenden Sie die DOS-Eingabeaufforderung.  
  
> [!NOTE]  
>  Da Oracle Fehler in aktuellen Versionen behebt und diese dann mithilfe von Softwarepatches auf frühere Versionen nachrüstet, wird empfohlen, den neuesten verfügbaren Patch herunterzuladen. Dies gilt insbesondere für die Oracle Server Client-Komponenten. Wenn Sie Fragen zur Installation dieser Patches haben, wenden Sie sich an den Oracle Support.
