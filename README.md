# 📋 Spring Audit Trail

[![Java](https://img.shields.io/badge/Java-21-orange)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4-brightgreen)](https://spring.io/projects/spring-boot)
[![RGPD](https://img.shields.io/badge/RGPD-Compliant-green)](https://gdpr.eu/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Bibliothèque d'audit trail automatique pour Spring Boot. Tracez toutes les actions utilisateurs pour conformité RGPD, sécurité, et secteurs réglementés.

## 🎯 Cas d'Usage

- ✅ **Conformité RGPD** : Traçabilité complète des accès données
- ✅ **Audit de sécurité** : Qui a fait quoi et quand
- ✅ **Secteur financier** : Piste d'audit réglementaire
- ✅ **Secteur public** : Transparence des actions

## 🚀 Quick Start

```java
@Service
public class UserService {

    @Audited(action = "USER_CREATION")
    public User createUser(CreateUserRequest request) {
        return userRepository.save(user);
    }

    @Audited(action = "USER_DELETION", sensitivity = HIGH)
    public void deleteUser(Long userId) {
        userRepository.deleteById(userId);
    }
}
```

## 📊 Résultat Automatique

| Timestamp | User | Action | Resource | IP | Details |
|-----------|------|--------|----------|----|---------|
| 2026-01-02 10:30 | admin@ex.com | USER_DELETION | User:123 | 192.168.1.1 | {reason: "GDPR request"} |

## 🔧 Fonctionnalités

✅ Annotation `@Audited` sur méthodes
✅ Capture automatique : user, timestamp, IP, user-agent
✅ Support RGPD : pseudonymisation, anonymisation
✅ Filtres personnalisables
✅ Export audit logs (JSON, CSV)
✅ Dashboard Kibana ready

## 📈 Conformité RGPD

```java
@Configuration
public class AuditConfig {

    @Bean
    public GdprAuditStrategy gdprStrategy() {
        return GdprAuditStrategy.builder()
            .pseudonymizeEmails(true)
            .retention(90, ChronoUnit.DAYS)
            .exportFormat(ExportFormat.JSON)
            .build();
    }
}
```

## 🏆 Cas d'Usage Réel

Utilisé en production sur systèmes fintech (MoneyTrack) et secteur public (UGAP) pour conformité RGPD et audits de sécurité.

**Bénéfices** :
- ✅ Conformité 100% RGPD
- ✅ Audits simplifiés
- ✅ Traçabilité complète

## 👤 Auteur

**Imad ATTAR** - Senior Java Architect | Security & Compliance Expert

Utilisé en production sur des systèmes critiques fintech et secteur public.

---

⭐ Star si ce projet simplifie vos audits de conformité !
