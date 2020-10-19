---
title: Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (Konfigurations-Manager) | Microsoft-Dokumentation
description: Reporting Services verwendet Verschlüsselungsschlüssel, um Anmelde- und Verbindungsinformationen zu sichern, die in einer Berichtsserver-Datenbank gespeichert sind.
ms.date: 12/04/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.custom: seo-lt-2019, seo-mmd-2019
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0c354b399b80e668261b95f8b65f987da547c855
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934732"
---
# <a name="configure-and-manage-encryption-keys-report-server-configuration-manager"></a>Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (Berichtsserver-Konfigurations-Manager)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet Verschlüsselungsschlüssel, um Anmelde- und Verbindungsinformationen zu sichern, die in einer Berichtsserver-Datenbank gespeichert sind. Die Verschlüsselung in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]besteht aus einer Kombination von öffentlichen, privaten und symmetrischen Schlüsseln, die zum Schutz sensibler Daten verwendet werden. Der symmetrische Schlüssel wird bei der Initialisierung des Berichtsservers erstellt, wenn Sie den Berichtsserver installieren oder konfigurieren. Er wird vom Berichtsserver verwendet, um sensible Daten zu verschlüsseln, die auf dem Berichtsserver gespeichert sind. Öffentliche und private Schlüssel werden vom Betriebssystem erstellt und zum Schutz des symmetrischen Schlüssels verwendet. Ein Paar aus einem privaten und einem öffentlichen Schlüssel wird für jede Berichtsserverinstanz erstellt, die sensible Daten in einer Berichtsserver-Datenbank speichert.  
  
 Zur Verwaltung der Verschlüsselungsschlüssel gehört das Erstellen einer Sicherungskopie des symmetrischen Schlüssels und das Wissen darüber, wann und wie die Schlüssel wiederhergestellt, gelöscht oder geändert werden müssen. Wenn Sie eine Berichtsserverinstallation migrieren oder eine Bereitstellung für dezentrales Skalieren konfigurieren, benötigen Sie eine Sicherungskopie des symmetrischen Schlüssels, sodass Sie ihn auf die neue Installation anwenden können.  
  
> [!IMPORTANT]  
>  Aus Sicherheitsgründen empfiehlt es sich, den Reporting Services-Verschlüsselungsschlüssel in regelmäßigen Abständen zu ändern. Ein guter Zeitpunkt, um den Schlüssel zu ändern, liegt direkt im Anschluss an ein größeres Versionsupgrade von Reporting Services. Indem der Schlüssel nach einem Upgrade geändert wird, lassen sich zusätzliche Dienstunterbrechungen, die durch eine Änderung des Reporting Services-Verschlüsselungsschlüssels außerhalb des Upgradezyklus verursacht würden, minimieren.  
  
 Symmetrische Schlüssel können mithilfe des Reporting Services-Konfigurationstools oder des Hilfsprogramms **rskeymgmt** verwaltet werden. Die in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthaltenen Tools werden nur zum Verwalten des symmetrischen Schlüssels verwendet (private und öffentliche Schlüssel werden vom Betriebssystem verwaltet). Sowohl das Reporting Services-Konfigurationstool als auch das Hilfsprogramm **rskeymgmt** unterstützen folgende Aufgaben:  
  
-   Erstellen einer Sicherungskopie des symmetrischen Schlüssels, sodass er zum Wiederherstellen einer Berichtsserverinstallation oder im Rahmen einer geplanten Migration verwendet werden kann.  
  
-   Wiederherstellen eines zuvor gespeicherten symmetrischen Schlüssels in einer Berichtsserver-Datenbank, sodass eine neue Berichtsserverinstanz auf die vorhandenen Daten zugreifen kann, die ursprünglich nicht von ihr verschlüsselt wurden.  
  
-   Löschen der verschlüsselten Daten in einer Berichtsserver-Datenbank in dem unwahrscheinlichen Fall, dass Sie nicht mehr auf die verschlüsselten Daten zugreifen können.  
  
-   Erneues Erstellen symmetrischer Schlüssel und erneutes Verschlüsseln von Daten in dem unwahrscheinlichen Fall, dass der symmetrische Schlüssel nicht mehr sicher ist. Eine bewährte Sicherheitsmethode ist die regelmäßige Neuerstellung des symmetrischen Schlüssels (z. B. alle paar Monate), um die Berichtsserver-Datenbank vor Angriffen aus dem Internet zu schützen, bei denen versucht wird, den Schlüssel zu entschlüsseln.  
  
-   Hinzufügen oder Entfernen einer Berichtsserverinstanz aus einer Berichtsserverbereitstellung für dezentrales Skalieren, bei der mehrere Berichtsserver eine einzige Berichtsserver-Datenbank und den symmetrischen Schlüssel, der für diese Datenbank die umkehrbare Verschlüsselung bereitstellt, gemeinsam nutzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Initialisieren eines Berichtsservers &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
 Erläutert das Erstellen von Verschlüsselungsschlüsseln.  
  
 [Verschlüsselungsschlüssel für SSRS: Sichern und Wiederherstellen von Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 Erläutert das Sichern von Verschlüsselungsschlüsseln und das Wiederherstellen dieser Schlüssel, um eine Berichtsserverinstallation wiederherzustellen oder zu migrieren.  
  
 [Speichern verschlüsselter Berichtsserverdaten &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 Beschreibt die Verschlüsselung auf einem Berichtsserver.  
  
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 Erläutert das Ersetzen eines symmetrischen Schlüssels durch eine neue Version und das erneute Erstellen, wenn die symmetrischen Schlüssel nicht überprüft werden können.  
  
 [Hinzufügen und Entfernen von Verschlüsselungsschlüsseln für die Bereitstellung für horizontales Skalieren &#40;Berichtsserver-Konfigurations-Manager&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 Beschreibt das Hinzufügen und Entfernen von Verschlüsselungsschlüsseln, um zu steuern, welche Berichtsserver Teil der Bereitstellung für dezentrales Skalieren sind.  
  
## <a name="see-also"></a>Weitere Informationen  
[Berichtsserver-Konfigurations-Manager (nativer Modus)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)
