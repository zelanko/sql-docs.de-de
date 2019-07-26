---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215611"
---
> [!NOTE]
> Wenn Sie die Ressource erstellen und danach der Pacemaker-Ressourcenagent in regelmäßigen Abständen den Wert von `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` automatisch auf die Verfügbarkeitsgruppe basierend auf der Konfiguration der Verfügbarkeitsgruppe festlegt. Wenn die Verfügbarkeitsgruppe z.B. über drei synchrone Replikate verfügt, wird der Agent `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf `1` festlegen. Details und weitere Konfigurationsoptionen finden Sie unter [High availability and data protection for availability group configurations (Hohe Verfügbarkeit und Schutz von Daten für Verfügbarkeitsgruppenkonfigurationen)](../linux/sql-server-linux-availability-group-ha.md). 