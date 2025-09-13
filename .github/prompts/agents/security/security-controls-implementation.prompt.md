---
name: security-controls-implementation
description: Design, implement, and operationalize comprehensive security controls with technology-adaptive protection strategies and defense-in-depth architecture
tools: [bash, glob, grep, read, edit, write, web_search, web_fetch]
model: claude-sonnet-4
---

# Security Controls Implementation Framework

## 🎯 Mission

Design, implement, and operationalize comprehensive security controls across the entire technology stack, ensuring defense-in-depth protection while maintaining usability and business functionality through systematic security engineering practices.

## 📋 Context-Adaptive Analysis Framework

### Initial Context Assessment

The security-engineer analyzes the copilot.instructions.md file to determine:
- **Technology Infrastructure**: Application architecture and deployment model (cloud, on-premise, hybrid) for appropriate security control selection and implementation
- **Application Stack**: Programming languages and frameworks for technology-specific security controls and integration patterns
- **Business Domain**: Industry-specific security requirements and compliance obligations for control framework selection
- **Project Scale**: Infrastructure complexity and user base for appropriate control granularity and automation levels
- **Security Maturity**: Existing security tools and processes for integration planning and control layering strategies

Based on this analysis, the security engineer will select appropriate security control frameworks, implement technology-specific protections, and ensure comprehensive defense-in-depth coverage across the entire technology stack.

## 📋 Comprehensive Security Control Framework

### Phase 1: Security Control Architecture Design (2-3 hours)

**Step 1.1: Defense-in-Depth Security Control Framework**

```python
# Defense-in-Depth Security Control Framework
SECURITY_CONTROL_LAYERS = {
    'physical_security': {
        'facility_controls': [
            'access_card_systems', 'biometric_controls', 'surveillance_systems',
            'environmental_monitoring', 'secure_destruction_facilities'
        ],
        'hardware_controls': [
            'secure_boot_processes', 'hardware_security_modules',
            'tamper_evident_seals', 'asset_tracking_systems'
        ]
    },
    'network_security': {
        'perimeter_controls': [
            'next_gen_firewalls', 'intrusion_prevention_systems',
            'ddos_protection', 'secure_remote_access_gateways'
        ],
        'internal_controls': [
            'network_segmentation', 'micro_segmentation', 'network_access_control',
            'network_monitoring', 'east_west_traffic_inspection'
        ]
    },
    'endpoint_security': {
        'device_controls': [
            'endpoint_detection_response', 'mobile_device_management',
            'disk_encryption', 'application_whitelisting', 'patch_management'
        ],
        'user_controls': [
            'privileged_access_management', 'multi_factor_authentication',
            'identity_governance', 'behavioral_analytics'
        ]
    },
    'application_security': {
        'development_controls': [
            'secure_coding_standards', 'static_analysis', 'dynamic_analysis',
            'dependency_scanning', 'secure_development_lifecycle'
        ],
        'runtime_controls': [
            'web_application_firewalls', 'runtime_application_protection',
            'api_security_gateways', 'container_security'
        ]
    },
    'data_security': {
        'data_protection_controls': [
            'data_classification', 'encryption_at_rest', 'encryption_in_transit',
            'data_loss_prevention', 'rights_management'
        ],
        'data_governance_controls': [
            'data_discovery', 'privacy_controls', 'retention_management',
            'audit_logging', 'data_masking'
        ]
    }
}

class SecurityControlArchitect:
    def __init__(self, business_requirements, threat_model):
        self.requirements = business_requirements
        self.threats = threat_model
        self.control_framework = {}

    def design_layered_security_architecture(self):
        """Design comprehensive defense-in-depth security architecture"""
        architecture_design = {
            'threat_aligned_controls': self._map_controls_to_threats(),
            'risk_based_prioritization': self._prioritize_controls_by_risk(),
            'integration_architecture': self._design_integration_patterns(),
            'monitoring_architecture': self._design_monitoring_framework(),
            'automation_framework': self._design_automation_capabilities()
        }

        return architecture_design

    def _map_controls_to_threats(self):
        """Map security controls to specific threat scenarios"""
        threat_control_mapping = {
            'advanced_persistent_threats': {
                'detection_controls': [
                    'behavioral_analytics_ueba', 'threat_hunting_platform',
                    'deception_technology', 'extended_detection_response_xdr'
                ],
                'prevention_controls': [
                    'zero_trust_architecture', 'privileged_access_management',
                    'application_control', 'network_segmentation'
                ],
                'response_controls': [
                    'security_orchestration_automation', 'incident_response_platform',
                    'forensic_tools', 'containment_automation'
                ]
            },
            'insider_threats': {
                'detection_controls': [
                    'user_behavior_analytics', 'data_access_monitoring',
                    'privileged_session_recording', 'anomaly_detection'
                ],
                'prevention_controls': [
                    'data_classification_labeling', 'rights_management',
                    'segregation_of_duties', 'approval_workflows'
                ],
                'deterrent_controls': [
                    'audit_logging', 'screen_recording', 'legal_agreements',
                    'security_awareness_training'
                ]
            },
            'external_attacks': {
                'perimeter_controls': [
                    'web_application_firewall', 'ddos_protection',
                    'threat_intelligence_feeds', 'email_security_gateway'
                ],
                'endpoint_controls': [
                    'endpoint_protection_platform', 'vulnerability_management',
                    'patch_management', 'configuration_management'
                ],
                'identity_controls': [
                    'identity_provider_integration', 'risk_based_authentication',
                    'session_management', 'account_lockout_policies'
                ]
            }
        }

        return threat_control_mapping

    def design_control_integration_framework(self):
        """Design comprehensive control integration and orchestration"""
        integration_framework = {
            'centralized_management': {
                'security_information_event_management': {
                    'platform_selection': 'splunk_qradar_sentinel_elastic_security',
                    'data_ingestion': 'real_time_log_streaming_api_integration',
                    'correlation_rules': 'mitre_attack_framework_mapping',
                    'alerting_workflows': 'priority_based_notification_escalation',
                    'dashboard_analytics': 'executive_operational_technical_views'
                },
                'security_orchestration_automation': {
                    'playbook_engine': 'phantom_demisto_swimlane_automation',
                    'incident_workflows': 'automated_response_human_approval_gates',
                    'integration_connectors': 'api_based_tool_integration',
                    'case_management': 'incident_tracking_forensic_evidence_collection'
                }
            },
            'threat_intelligence_platform': {
                'intelligence_sources': {
                    'commercial_feeds': 'crowdstrike_recorded_future_anomali_threatq',
                    'open_source_feeds': 'misp_otx_virustotal_alienvault',
                    'government_feeds': 'us_cert_ncsc_sector_specific_sharing',
                    'internal_intelligence': 'incident_iocs_hunting_discoveries'
                },
                'intelligence_processing': {
                    'normalization': 'stix_taxii_standardized_format_conversion',
                    'enrichment': 'context_attribution_confidence_scoring',
                    'validation': 'false_positive_filtering_source_reputation',
                    'distribution': 'automated_security_control_updates'
                }
            }
        }

        return integration_framework
```

**Step 1.2: Technology Integration and Orchestration**

```python
class SecurityControlIntegrationFramework:
    def __init__(self, existing_infrastructure, security_tools):
        self.infrastructure = existing_infrastructure
        self.tools = security_tools

    def design_siem_integration_architecture(self):
        """Design comprehensive SIEM integration with all security tools"""
        siem_integration = {
            'data_ingestion_architecture': {
                'log_sources': {
                    'network_devices': {
                        'firewalls': 'syslog_cef_format_real_time',
                        'switches_routers': 'snmp_netflow_sflow_real_time',
                        'wireless_controllers': 'syslog_radius_accounting',
                        'load_balancers': 'syslog_http_access_logs'
                    },
                    'security_tools': {
                        'endpoint_protection': 'api_json_real_time_alerts',
                        'vulnerability_scanners': 'api_xml_scheduled_pulls',
                        'identity_providers': 'api_oauth_real_time_events',
                        'cloud_platforms': 'api_cloudtrail_continuous_streaming'
                    },
                    'business_applications': {
                        'web_applications': 'syslog_application_logs',
                        'databases': 'database_audit_logs_real_time',
                        'erp_systems': 'api_business_transaction_logs',
                        'collaboration_tools': 'api_user_activity_logs'
                    }
                },
                'data_normalization': {
                    'common_event_format': 'cef_standardized_field_mapping',
                    'taxonomy_mapping': 'mitre_att_ck_technique_mapping',
                    'threat_intelligence_enrichment': 'ioc_reputation_context_addition',
                    'asset_context_enrichment': 'cmdb_user_directory_integration'
                }
            },
            'correlation_and_analytics': {
                'real_time_correlation_rules': {
                    'authentication_anomalies': 'impossible_travel_brute_force_detection',
                    'lateral_movement_detection': 'kerberos_smb_rdp_anomaly_correlation',
                    'data_exfiltration_patterns': 'large_file_transfers_unusual_destinations',
                    'privilege_escalation': 'account_modification_privilege_changes'
                },
                'machine_learning_analytics': {
                    'user_behavior_baselines': 'unsupervised_clustering_normal_patterns',
                    'anomaly_detection': 'supervised_learning_known_attack_patterns',
                    'threat_hunting': 'graph_analytics_relationship_discovery',
                    'predictive_analytics': 'risk_scoring_attack_probability'
                }
            }
        }

        return siem_integration

    def implement_security_orchestration(self):
        """Implement comprehensive security orchestration and automation"""
        orchestration_framework = {
            'playbook_automation': {
                'incident_response_playbooks': {
                    'malware_detection': {
                        'trigger': 'edr_malware_alert_confidence_high',
                        'automated_actions': [
                            'isolate_endpoint_network_quarantine',
                            'collect_forensic_triage_package',
                            'notify_security_team_escalation',
                            'create_incident_ticket_documentation',
                            'initiate_threat_hunting_related_systems'
                        ],
                        'approval_gates': 'manager_approval_before_system_wipe',
                        'rollback_procedures': 'restore_endpoint_if_false_positive'
                    },
                    'credential_compromise': {
                        'trigger': 'multiple_failed_logins_password_spray',
                        'automated_actions': [
                            'lock_user_account_temporary_disable',
                            'invalidate_existing_sessions_tokens',
                            'require_password_reset_mfa_setup',
                            'notify_user_manager_security_team',
                            'initiate_account_activity_review'
                        ],
                        'approval_gates': 'security_analyst_validation_required',
                        'rollback_procedures': 'unlock_account_if_legitimate_activity'
                    },
                    'data_exfiltration_attempt': {
                        'trigger': 'dlp_large_data_transfer_unusual_destination',
                        'automated_actions': [
                            'block_network_connection_immediate',
                            'quarantine_source_endpoint_isolation',
                            'preserve_network_forensic_evidence',
                            'escalate_to_incident_response_team',
                            'initiate_data_breach_assessment'
                        ],
                        'approval_gates': 'legal_team_breach_notification_decision',
                        'rollback_procedures': 'restore_access_if_false_positive'
                    }
                },
                'threat_intelligence_automation': {
                    'ioc_processing': {
                        'feed_ingestion': 'automated_threat_feed_consumption',
                        'ioc_validation': 'reputation_scoring_false_positive_filtering',
                        'distribution': 'automatic_firewall_dns_sinkhole_updates',
                        'hunting': 'retroactive_search_historical_data',
                        'reporting': 'automated_threat_landscape_reports'
                    },
                    'vulnerability_management': {
                        'scan_orchestration': 'scheduled_authenticated_comprehensive_scanning',
                        'prioritization': 'cvss_epss_business_impact_risk_scoring',
                        'patch_management': 'automated_patch_testing_deployment',
                        'exception_handling': 'risk_acceptance_compensating_controls'
                    }
                }
            }
        }

        return orchestration_framework
```

### Phase 2: Identity and Access Control Implementation (3-4 hours)

**Step 2.1: Zero Trust Identity Architecture**

```python
class ZeroTrustIdentityFramework:
    def __init__(self, user_directory, application_inventory):
        self.users = user_directory
        self.applications = application_inventory

    def implement_identity_governance(self):
        """Implement comprehensive identity governance and administration"""
        identity_governance = {
            'identity_lifecycle_management': {
                'user_provisioning': {
                    'automated_onboarding': {
                        'trigger': 'hr_system_new_employee_webhook',
                        'process': [
                            'create_active_directory_account',
                            'assign_role_based_group_memberships',
                            'provision_email_collaboration_accounts',
                            'generate_temporary_credentials',
                            'send_welcome_package_training_links'
                        ],
                        'approval_workflow': 'manager_hr_security_three_way_approval',
                        'audit_trail': 'complete_provisioning_activity_logging'
                    },
                    'role_changes': {
                        'trigger': 'hr_system_role_change_promotion_transfer',
                        'process': [
                            'analyze_current_access_rights',
                            'determine_new_access_requirements',
                            'implement_least_privilege_principle',
                            'remove_obsolete_access_rights',
                            'notify_stakeholders_of_changes'
                        ],
                        'approval_workflow': 'new_manager_security_approval_required',
                        'validation': 'access_recertification_within_30_days'
                    },
                    'user_deprovisioning': {
                        'trigger': 'hr_system_termination_resignation_webhook',
                        'immediate_actions': [
                            'disable_all_user_accounts',
                            'revoke_all_access_tokens_sessions',
                            'disable_vpn_remote_access',
                            'flag_user_data_for_backup_retention',
                            'notify_it_security_managers'
                        ],
                        'delayed_actions': [
                            'transfer_data_ownership_new_assignee',
                            'delete_personal_user_data_gdpr_compliance',
                            'return_company_assets_device_wipe',
                            'complete_exit_interview_security_briefing'
                        ]
                    }
                },
                'access_certification': {
                    'periodic_reviews': {
                        'frequency': 'quarterly_role_based_semi_annual_privileged',
                        'scope': 'all_application_access_data_access_admin_rights',
                        'reviewers': 'data_owners_managers_security_team',
                        'automation': 'ai_assisted_anomaly_flagging',
                        'enforcement': 'auto_revoke_uncertified_access_30_days'
                    },
                    'event_driven_reviews': {
                        'triggers': [
                            'role_change_promotion_transfer',
                            'security_incident_account_compromise',
                            'compliance_audit_external_review',
                            'data_breach_privileged_account_exposure'
                        ],
                        'scope': 'risk_based_expanded_review_related_accounts',
                        'urgency': 'complete_within_48_hours_critical_systems'
                    }
                }
            },
            'privileged_access_management': {
                'privileged_account_discovery': {
                    'scanning_scope': 'all_systems_applications_databases_network_devices',
                    'identification_methods': [
                        'active_directory_privileged_group_enumeration',
                        'database_sysadmin_role_identification',
                        'application_admin_account_discovery',
                        'service_account_privileged_access_mapping'
                    ],
                    'risk_assessment': 'criticality_exposure_usage_frequency_scoring'
                },
                'password_vaulting': {
                    'vault_architecture': 'high_availability_encrypted_vault_cluster',
                    'access_controls': 'dual_person_integrity_manager_approval',
                    'session_recording': 'full_session_video_keystroke_recording',
                    'password_rotation': 'automated_30_day_rotation_policy',
                    'emergency_access': 'break_glass_procedures_full_audit_trail'
                },
                'just_in_time_access': {
                    'implementation': 'temporary_group_membership_elevation',
                    'approval_workflow': 'business_justification_manager_security_approval',
                    'time_limits': 'maximum_8_hours_automatic_revocation',
                    'monitoring': 'continuous_activity_monitoring_privileged_sessions',
                    'attestation': 'post_access_activity_justification_required'
                }
            }
        }

        return identity_governance

    def implement_advanced_authentication(self):
        """Implement risk-based adaptive authentication"""
        authentication_framework = {
            'multi_factor_authentication': {
                'factor_types': {
                    'knowledge_factors': 'passwords_passphrases_security_questions',
                    'possession_factors': 'hardware_tokens_mobile_apps_smart_cards',
                    'inherence_factors': 'biometrics_fingerprint_face_voice_recognition',
                    'location_factors': 'gps_network_location_device_registration',
                    'behavioral_factors': 'keystroke_dynamics_mouse_movement_patterns'
                },
                'adaptive_policies': {
                    'low_risk_scenarios': {
                        'conditions': 'known_device_trusted_network_normal_hours',
                        'requirements': 'single_factor_password_only',
                        'monitoring': 'passive_behavioral_analytics'
                    },
                    'medium_risk_scenarios': {
                        'conditions': 'new_device_vpn_access_after_hours',
                        'requirements': 'two_factor_password_plus_mobile_app',
                        'monitoring': 'enhanced_session_monitoring'
                    },
                    'high_risk_scenarios': {
                        'conditions': 'foreign_country_tor_exit_node_privileged_access',
                        'requirements': 'three_factor_password_token_biometric',
                        'monitoring': 'real_time_security_analyst_review'
                    }
                }
            },
            'single_sign_on_architecture': {
                'identity_provider': 'saml_oauth_openid_connect_federation',
                'application_integration': 'pre_built_connectors_custom_integration',
                'session_management': 'centralized_session_timeout_policies',
                'federation_trusts': 'b2b_partner_customer_identity_federation',
                'security_controls': 'token_encryption_signature_validation_replay_protection'
            }
        }

        return authentication_framework
```

**Step 2.2: Application Security Controls**

```python
class ApplicationSecurityControlFramework:
    def __init__(self, application_portfolio, development_practices):
        self.applications = application_portfolio
        self.dev_practices = development_practices

    def implement_application_protection(self):
        """Implement comprehensive application security controls"""
        app_security_controls = {
            'web_application_firewall': {
                'deployment_architecture': {
                    'cloud_native_waf': 'aws_cloudflare_azure_front_door',
                    'on_premise_waf': 'f5_asm_imperva_securesphere',
                    'hybrid_deployment': 'consistent_policy_management_across_environments'
                },
                'protection_capabilities': {
                    'owasp_top_10_protection': 'injection_xss_csrf_security_misconfiguration',
                    'api_protection': 'rest_graphql_soap_api_specific_rules',
                    'bot_protection': 'malicious_bot_detection_captcha_challenge',
                    'ddos_protection': 'application_layer_ddos_mitigation',
                    'threat_intelligence': 'real_time_reputation_feeds_integration'
                },
                'advanced_features': {
                    'behavioral_analysis': 'anomaly_detection_user_behavior_profiling',
                    'machine_learning': 'adaptive_rules_false_positive_reduction',
                    'custom_rules': 'application_specific_business_logic_protection',
                    'virtual_patching': 'immediate_protection_before_code_fixes'
                }
            },
            'runtime_application_protection': {
                'rasp_deployment': {
                    'agent_based': 'application_server_embedded_protection',
                    'agentless': 'network_based_traffic_inspection',
                    'container_integration': 'kubernetes_sidecar_istio_service_mesh'
                },
                'protection_mechanisms': {
                    'code_injection_prevention': 'sql_injection_command_injection_detection',
                    'deserialization_protection': 'unsafe_deserialization_attack_prevention',
                    'file_upload_security': 'malware_scanning_file_type_validation',
                    'session_protection': 'session_hijacking_fixation_prevention'
                }
            },
            'api_security_gateway': {
                'api_discovery': 'automatic_api_endpoint_documentation_discovery',
                'authentication_authorization': 'oauth_jwt_api_key_management',
                'rate_limiting': 'per_user_per_api_adaptive_rate_limiting',
                'monitoring_analytics': 'api_usage_patterns_anomaly_detection',
                'data_protection': 'sensitive_data_masking_tokenization'
            }
        }

        return app_security_controls

    def implement_secure_development_controls(self):
        """Implement security controls in development pipeline"""
        dev_security_controls = {
            'secure_code_analysis': {
                'static_analysis': {
                    'tools': 'checkmarx_veracode_sonarqube_semgrep',
                    'integration': 'ide_plugins_git_hooks_ci_cd_pipeline',
                    'coverage': 'all_languages_frameworks_custom_rules',
                    'remediation': 'developer_guidance_fix_recommendations'
                },
                'dynamic_analysis': {
                    'tools': 'owasp_zap_burp_suite_rapid7_appspider',
                    'automation': 'automated_scanning_ci_cd_integration',
                    'coverage': 'authenticated_scanning_complete_application_flow',
                    'reporting': 'vulnerability_prioritization_false_positive_filtering'
                },
                'interactive_analysis': {
                    'tools': 'contrast_security_hdiv_protection_prevoty',
                    'runtime_feedback': 'real_time_vulnerability_detection',
                    'accuracy': 'reduced_false_positives_context_awareness',
                    'integration': 'development_testing_production_environments'
                }
            },
            'dependency_security_management': {
                'vulnerability_scanning': {
                    'tools': 'snyk_blackduck_whitesource_dependabot',
                    'coverage': 'direct_transitive_dependencies_container_images',
                    'automation': 'continuous_monitoring_pull_request_checking',
                    'remediation': 'automated_dependency_updates_security_patches'
                },
                'license_compliance': {
                    'scanning': 'open_source_license_identification',
                    'policy_enforcement': 'approved_restricted_prohibited_licenses',
                    'reporting': 'compliance_dashboards_legal_review_workflows',
                    'alternatives': 'alternative_component_recommendations'
                }
            }
        }

        return dev_security_controls
```

### Phase 3: Data Protection and Monitoring Implementation (2-3 hours)

**Step 3.1: Comprehensive Data Protection Framework**

```python
class DataProtectionFramework:
    def __init__(self, data_inventory, regulatory_requirements):
        self.data_catalog = data_inventory
        self.regulations = regulatory_requirements

    def implement_data_classification_protection(self):
        """Implement automated data classification and protection"""
        data_protection_controls = {
            'data_discovery_classification': {
                'automated_discovery': {
                    'structured_data': 'database_table_column_scanning_regex_patterns',
                    'unstructured_data': 'file_shares_email_document_content_analysis',
                    'cloud_storage': 'aws_s3_azure_blob_gcp_storage_scanning',
                    'application_data': 'api_endpoint_data_flow_analysis'
                },
                'classification_engine': {
                    'pattern_matching': 'regex_patterns_ssn_credit_card_patterns',
                    'machine_learning': 'nlp_content_classification_context_analysis',
                    'metadata_analysis': 'file_names_directory_structure_patterns',
                    'user_input': 'manual_classification_validation_feedback'
                },
                'classification_labels': {
                    'public': 'marketing_materials_public_website_content',
                    'internal': 'policies_procedures_internal_communications',
                    'confidential': 'financial_data_hr_records_customer_data',
                    'restricted': 'trade_secrets_legal_privileged_regulated_data'
                }
            },
            'encryption_implementation': {
                'encryption_at_rest': {
                    'database_encryption': 'tde_column_level_field_level_encryption',
                    'file_system_encryption': 'full_disk_encryption_file_level_encryption',
                    'backup_encryption': 'encrypted_backup_secure_key_management',
                    'key_management': 'hardware_security_modules_key_rotation'
                },
                'encryption_in_transit': {
                    'network_encryption': 'tls_1_3_ipsec_vpn_secure_protocols',
                    'application_encryption': 'end_to_end_message_encryption',
                    'api_encryption': 'https_certificate_pinning_mutual_tls',
                    'database_connections': 'encrypted_database_connections_ssl'
                },
                'key_management_service': {
                    'centralized_kms': 'aws_kms_azure_key_vault_hashicorp_vault',
                    'key_lifecycle': 'generation_rotation_revocation_destruction',
                    'access_controls': 'role_based_key_access_dual_control',
                    'audit_logging': 'complete_key_usage_access_audit_trail'
                }
            },
            'data_loss_prevention': {
                'network_dlp': {
                    'email_protection': 'outbound_email_scanning_attachment_analysis',
                    'web_protection': 'http_https_upload_monitoring_blocking',
                    'cloud_protection': 'saas_application_data_upload_monitoring',
                    'removable_media': 'usb_device_control_data_transfer_blocking'
                },
                'endpoint_dlp': {
                    'agent_deployment': 'windows_mac_linux_endpoint_agents',
                    'content_inspection': 'file_content_clipboard_screen_capture_monitoring',
                    'policy_enforcement': 'block_warn_allow_custom_actions',
                    'offline_protection': 'cached_policies_disconnected_enforcement'
                }
            }
        }

        return data_protection_controls

    def implement_privacy_controls(self):
        """Implement privacy by design controls"""
        privacy_controls = {
            'consent_management': {
                'consent_capture': 'granular_purpose_specific_consent_collection',
                'consent_storage': 'immutable_audit_trail_consent_decisions',
                'consent_withdrawal': 'easy_withdrawal_mechanisms_honor_requests',
                'consent_analytics': 'consent_rates_withdrawal_trends_analysis'
            },
            'data_subject_rights': {
                'right_of_access': 'automated_data_subject_access_request_fulfillment',
                'right_to_rectification': 'data_correction_workflows_verification',
                'right_to_erasure': 'automated_data_deletion_right_to_be_forgotten',
                'data_portability': 'structured_data_export_standard_formats'
            },
            'privacy_impact_assessments': {
                'automated_screening': 'high_risk_processing_activity_identification',
                'impact_analysis': 'privacy_risk_assessment_mitigation_planning',
                'stakeholder_consultation': 'dpo_legal_business_stakeholder_review',
                'monitoring': 'ongoing_privacy_impact_monitoring_updates'
            }
        }

        return privacy_controls
```

**Step 3.2: Security Monitoring and Analytics**

```python
class SecurityMonitoringFramework:
    def __init__(self, infrastructure_scale, security_requirements):
        self.scale = infrastructure_scale
        self.requirements = security_requirements

    def implement_comprehensive_monitoring(self):
        """Implement comprehensive security monitoring and analytics"""
        monitoring_architecture = {
            'extended_detection_response': {
                'data_collection': {
                    'endpoint_telemetry': 'process_network_file_registry_activity',
                    'network_telemetry': 'flow_records_packet_inspection_dns_logs',
                    'cloud_telemetry': 'api_calls_resource_changes_access_patterns',
                    'identity_telemetry': 'authentication_authorization_privilege_usage'
                },
                'advanced_analytics': {
                    'behavioral_analysis': 'ml_models_baseline_deviation_detection',
                    'threat_hunting': 'hypothesis_driven_proactive_threat_search',
                    'attack_path_analysis': 'graph_analytics_lateral_movement_detection',
                    'attribution_analysis': 'ttp_mapping_threat_actor_identification'
                },
                'automated_response': {
                    'containment_actions': 'automatic_isolation_quarantine_blocking',
                    'investigation_automation': 'evidence_collection_timeline_reconstruction',
                    'notification_escalation': 'stakeholder_notification_escalation_workflows',
                    'remediation_orchestration': 'automated_remediation_action_execution'
                }
            },
            'threat_intelligence_platform': {
                'intelligence_feeds': {
                    'commercial_feeds': 'crowdstrike_recorded_future_anomali',
                    'open_source_feeds': 'misp_otx_virustotal_abuse_ch',
                    'government_feeds': 'us_cert_ncsc_sector_specific_intel',
                    'internal_intelligence': 'incident_artifacts_ioc_generation'
                },
                'intelligence_processing': {
                    'normalization': 'stix_taxii_standard_format_conversion',
                    'enrichment': 'context_addition_confidence_scoring',
                    'validation': 'false_positive_filtering_source_reputation',
                    'distribution': 'automated_security_tool_integration'
                }
            },
            'security_metrics_kpis': {
                'operational_metrics': {
                    'mean_time_to_detection': 'average_time_incident_first_indicator',
                    'mean_time_to_response': 'average_time_response_action_initiated',
                    'mean_time_to_containment': 'average_time_threat_contained',
                    'false_positive_rate': 'percentage_false_alerts_total_alerts'
                },
                'effectiveness_metrics': {
                    'coverage_assessment': 'mitre_att_ck_technique_coverage_percentage',
                    'detection_accuracy': 'true_positive_rate_precision_recall',
                    'threat_hunting_success': 'proactive_threats_discovered_percentage',
                    'incident_prevention': 'attacks_blocked_before_impact'
                }
            }
        }

        return monitoring_architecture
```

## 🔧 Technology-Adaptive Implementation

### Java/Spring Boot Security Controls

**Recommended Pattern:** Enterprise security with comprehensive monitoring and automated response

```java
// SecurityConfiguration.java - Comprehensive Spring Security setup
@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true, securedEnabled = true)
public class EnterpriseSecurityConfiguration {

    @Autowired
    private SecurityEventRepository securityEventRepository;

    @Autowired
    private ThreatDetectionService threatDetectionService;

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .csrf(csrf -> csrf
                .csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse())
                .ignoringRequestMatchers("/api/public/**")
            )
            .sessionManagement(session -> session
                .sessionCreationPolicy(SessionCreationPolicy.IF_REQUIRED)
                .maximumSessions(3)
                .maxSessionsPreventsLogins(false)
                .sessionRegistry(sessionRegistry())
                .and()
                .sessionFixation().migrateSession()
                .invalidSessionUrl("/login?expired")
            )
            .authorizeHttpRequests(authz -> authz
                // Public endpoints
                .requestMatchers("/api/public/**", "/health/**").permitAll()

                // Authentication endpoints
                .requestMatchers("/api/auth/login", "/api/auth/register").permitAll()

                // Role-based access control
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .requestMatchers("/api/users/**").hasAnyRole("USER", "ADMIN")
                .requestMatchers(HttpMethod.POST, "/api/data/**").hasAuthority("DATA_WRITE")
                .requestMatchers(HttpMethod.GET, "/api/reports/**").hasAuthority("REPORT_READ")

                // Default authentication required
                .anyRequest().authenticated()
            )
            .oauth2ResourceServer(oauth2 -> oauth2
                .jwt(jwt -> jwt
                    .decoder(jwtDecoder())
                    .jwtAuthenticationConverter(customJwtAuthenticationConverter())
                )
            )
            .headers(headers -> headers
                .frameOptions().deny()
                .contentTypeOptions().and()
                .httpStrictTransportSecurity(hsts -> hsts
                    .maxAgeInSeconds(31536000)
                    .includeSubdomains(true)
                    .preload(true)
                )
                .and()
                .addHeaderWriter(new StaticHeadersWriter(
                    "Content-Security-Policy",
                    "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'"
                ))
            );

        // Custom security filters
        http.addFilterBefore(new ThreatDetectionFilter(threatDetectionService),
                            UsernamePasswordAuthenticationFilter.class);
        http.addFilterAfter(new SecurityAuditFilter(securityEventRepository),
                           SecurityContextPersistenceFilter.class);

        return http.build();
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder(12);
    }
}

// SecurityAuditService.java - Comprehensive security event logging
@Service
@Transactional
public class SecurityAuditService {

    private static final Logger logger = LoggerFactory.getLogger(SecurityAuditService.class);

    @Autowired
    private SecurityEventRepository securityEventRepository;

    @Autowired
    private ThreatAnalysisService threatAnalysisService;

    @EventListener
    public void handleAuthenticationSuccess(AuthenticationSuccessEvent event) {
        SecurityEvent securityEvent = SecurityEvent.builder()
            .eventType(SecurityEventType.AUTHENTICATION_SUCCESS)
            .username(event.getAuthentication().getName())
            .timestamp(Instant.now())
            .ipAddress(getClientIpAddress())
            .userAgent(getCurrentUserAgent())
            .details("User successfully authenticated")
            .sessionId(getSessionId())
            .build();

        securityEventRepository.save(securityEvent);

        // Perform post-authentication security analysis
        threatAnalysisService.analyzeAuthenticationEvent(securityEvent);
    }

    @EventListener
    public void handleAuthenticationFailure(AbstractAuthenticationFailureEvent event) {
        String username = event.getAuthentication().getName();
        String reason = event.getException().getMessage();
        String clientIp = getClientIpAddress();

        SecurityEvent securityEvent = SecurityEvent.builder()
            .eventType(SecurityEventType.AUTHENTICATION_FAILURE)
            .username(username)
            .timestamp(Instant.now())
            .ipAddress(clientIp)
            .reason(reason)
            .userAgent(getCurrentUserAgent())
            .build();

        securityEventRepository.save(securityEvent);

        // Immediate threat analysis for failed authentications
        CompletableFuture.runAsync(() -> {
            try {
                boolean isThreat = threatAnalysisService.analyzeBruteForcePattern(username, clientIp);
                if (isThreat) {
                    triggerSecurityResponse(securityEvent);
                }
            } catch (Exception e) {
                logger.error("Failed to analyze authentication failure", e);
            }
        });
    }

    @Async
    public void triggerSecurityResponse(SecurityEvent securityEvent) {
        // Implement automated response based on threat level
        switch (securityEvent.getThreatLevel()) {
            case CRITICAL:
                handleCriticalThreat(securityEvent);
                break;
            case HIGH:
                handleHighThreat(securityEvent);
                break;
            case MEDIUM:
                handleMediumThreat(securityEvent);
                break;
        }
    }

    private void handleCriticalThreat(SecurityEvent event) {
        // Immediate account lockdown
        userManagementService.lockAccount(event.getUsername());

        // IP blocking
        firewallService.blockIpAddress(event.getIpAddress());

        // Immediate security team notification
        notificationService.sendSecurityAlert(
            SecurityAlert.builder()
                .severity(AlertSeverity.CRITICAL)
                .title("Critical Security Threat Detected")
                .description(String.format("Critical threat from IP %s targeting user %s",
                    event.getIpAddress(), event.getUsername()))
                .timestamp(event.getTimestamp())
                .requiresImmedateAction(true)
                .build()
        );

        // Start forensic evidence collection
        forensicsService.initiateIncidentResponse(event);
    }
}

// DataProtectionService.java - Advanced data protection implementation
@Service
public class DataProtectionService {

    private static final Logger logger = LoggerFactory.getLogger(DataProtectionService.class);

    @Autowired
    private KeyManagementService keyManagementService;

    @Autowired
    private DataClassificationService dataClassificationService;

    @PreAuthorize("hasPermission(#dataType, 'ENCRYPT')")
    public EncryptedData encryptSensitiveData(String plaintext, DataType dataType,
                                             String userContext) {
        try {
            // Classify data sensitivity
            DataClassification classification = dataClassificationService.classify(plaintext, dataType);

            // Select encryption algorithm based on classification
            EncryptionAlgorithm algorithm = selectEncryptionAlgorithm(classification);

            // Get context-aware encryption key
            EncryptionKey key = keyManagementService.getEncryptionKey(
                dataType, classification, userContext
            );

            // Perform authenticated encryption
            byte[] encrypted = performAuthenticatedEncryption(
                plaintext.getBytes(StandardCharsets.UTF_8), key, algorithm
            );

            EncryptedData result = EncryptedData.builder()
                .ciphertext(Base64.getEncoder().encodeToString(encrypted))
                .algorithm(algorithm.getName())
                .keyId(key.getKeyId())
                .dataClassification(classification)
                .encryptionTimestamp(Instant.now())
                .userContext(userContext)
                .build();

            // Audit encryption operation
            auditService.logDataEncryption(dataType, classification, userContext);

            return result;

        } catch (Exception e) {
            logger.error("Data encryption failed for type: {} context: {}", dataType, userContext, e);
            throw new DataProtectionException("Encryption operation failed", e);
        }
    }

    @PreAuthorize("hasPermission(#encryptedData.dataClassification, 'DECRYPT')")
    public String decryptSensitiveData(EncryptedData encryptedData, String userContext) {
        try {
            // Verify decryption authorization
            verifyDecryptionAuthorization(encryptedData, userContext);

            // Get decryption key
            EncryptionKey key = keyManagementService.getDecryptionKey(encryptedData.getKeyId());

            // Perform decryption
            byte[] decrypted = performAuthenticatedDecryption(
                Base64.getDecoder().decode(encryptedData.getCiphertext()),
                key,
                EncryptionAlgorithm.fromName(encryptedData.getAlgorithm())
            );

            String plaintext = new String(decrypted, StandardCharsets.UTF_8);

            // Audit decryption access
            auditService.logDataDecryption(encryptedData.getDataClassification(),
                userContext, SecurityContextHolder.getContext().getAuthentication().getName());

            return plaintext;

        } catch (Exception e) {
            logger.error("Data decryption failed for keyId: {} context: {}",
                encryptedData.getKeyId(), userContext, e);
            throw new DataProtectionException("Decryption operation failed", e);
        }
    }
}
```

### .NET Core Security Implementation

**Recommended Pattern:** Comprehensive ASP.NET Core security with advanced monitoring

```csharp
// SecurityConfiguration.cs
public class EnterpriseSecurityConfiguration
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Advanced Identity Configuration
        services.AddIdentity<ApplicationUser, ApplicationRole>(options =>
        {
            // Enhanced password policy
            options.Password.RequiredLength = 14;
            options.Password.RequireDigit = true;
            options.Password.RequireUppercase = true;
            options.Password.RequireLowercase = true;
            options.Password.RequireNonAlphanumeric = true;
            options.Password.RequiredUniqueChars = 6;

            // Progressive lockout policy
            options.Lockout.MaxFailedAccessAttempts = 3;
            options.Lockout.DefaultLockoutTimeSpan = TimeSpan.FromMinutes(30);
            options.Lockout.AllowedForNewUsers = true;

            // User validation requirements
            options.User.RequireUniqueEmail = true;
            options.SignIn.RequireConfirmedEmail = true;
            options.SignIn.RequireConfirmedAccount = true;
        })
        .AddEntityFrameworkStores<SecurityDbContext>()
        .AddDefaultTokenProviders()
        .AddPasswordValidator<EnterprisePasswordValidator<ApplicationUser>>();

        // JWT with enhanced security
        services.AddAuthentication(options =>
        {
            options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
            options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
        })
        .AddJwtBearer(options =>
        {
            options.RequireHttpsMetadata = true;
            options.SaveToken = true;
            options.TokenValidationParameters = new TokenValidationParameters
            {
                ValidateIssuerSigningKey = true,
                IssuerSigningKey = new SymmetricSecurityKey(
                    Encoding.UTF8.GetBytes(Configuration["Jwt:SecretKey"])),
                ValidateIssuer = true,
                ValidIssuer = Configuration["Jwt:Issuer"],
                ValidateAudience = true,
                ValidAudience = Configuration["Jwt:Audience"],
                ValidateLifetime = true,
                ClockSkew = TimeSpan.Zero,
                RequireExpirationTime = true,
                RequireSignedTokens = true
            };

            options.Events = new JwtBearerEvents
            {
                OnAuthenticationFailed = async context =>
                {
                    var securityMonitor = context.HttpContext.RequestServices
                        .GetRequiredService<ISecurityMonitoringService>();
                    await securityMonitor.HandleAuthenticationFailureAsync(context);
                },
                OnTokenValidated = async context =>
                {
                    var threatDetection = context.HttpContext.RequestServices
                        .GetRequiredService<IThreatDetectionService>();
                    await threatDetection.AnalyzeAuthenticatedRequestAsync(context);
                }
            };
        });

        // Comprehensive authorization policies
        services.AddAuthorization(options =>
        {
            // Multi-factor authentication requirements
            options.AddPolicy("RequireMFA", policy =>
                policy.RequireClaim("mfa_verified", "true"));

            // Data classification access
            options.AddPolicy("AccessConfidentialData", policy =>
                policy.Requirements.Add(new DataClassificationRequirement("Confidential")));

            // Time-based access controls
            options.AddPolicy("BusinessHoursOnly", policy =>
                policy.Requirements.Add(new BusinessHoursRequirement()));

            // Geographic access controls
            options.AddPolicy("DomesticAccessOnly", policy =>
                policy.Requirements.Add(new GeographicAccessRequirement("US")));
        });

        // Security services
        services.AddScoped<IThreatDetectionService, ThreatDetectionService>();
        services.AddScoped<IDataProtectionService, DataProtectionService>();
        services.AddScoped<ISecurityAuditService, SecurityAuditService>();
        services.AddScoped<IIncidentResponseService, IncidentResponseService>();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        // Comprehensive security headers
        app.UseSecurityHeaders(policies =>
            policies.AddFrameOptionsDeny()
                   .AddContentTypeOptionsNoSniff()
                   .AddStrictTransportSecurityMaxAgeIncludeSubDomains(maxAgeInSeconds: 31536000)
                   .AddReferrerPolicyStrictOriginWhenCrossOrigin()
                   .AddXSSProtectionBlock()
                   .AddContentSecurityPolicy(builder =>
                   {
                       builder.AddObjectSrc().None();
                       builder.AddFormAction().Self();
                       builder.AddFrameAncestors().None();
                       builder.AddBaseUri().Self();
                       builder.AddScriptSrc().Self().UnsafeInline();
                       builder.AddStyleSrc().Self().UnsafeInline();
                   }));

        // Advanced security middleware stack
        app.UseMiddleware<ThreatDetectionMiddleware>();
        app.UseMiddleware<DataProtectionMiddleware>();
        app.UseMiddleware<SecurityAuditMiddleware>();
        app.UseMiddleware<RateLimitingMiddleware>();
        app.UseMiddleware<GeoLocationFilterMiddleware>();

        app.UseAuthentication();
        app.UseAuthorization();
    }
}

// ThreatDetectionService.cs
public class ThreatDetectionService : IThreatDetectionService
{
    private readonly ISecurityEventRepository _securityEventRepository;
    private readonly IThreatIntelligenceService _threatIntelligence;
    private readonly ILogger<ThreatDetectionService> _logger;
    private readonly IConfiguration _configuration;

    public async Task<ThreatAssessment> AnalyzeRequestThreatAsync(HttpContext context, string username)
    {
        var assessment = new ThreatAssessment
        {
            Username = username,
            IpAddress = GetClientIpAddress(context),
            UserAgent = context.Request.Headers["User-Agent"].ToString(),
            RequestPath = context.Request.Path,
            HttpMethod = context.Request.Method,
            Timestamp = DateTime.UtcNow
        };

        // Multi-dimensional threat analysis
        await AnalyzeIpReputationAsync(assessment);
        await AnalyzeUserBehaviorAsync(assessment, context);
        await AnalyzeGeolocationRiskAsync(assessment);
        await AnalyzeDeviceFingerprintAsync(assessment, context);
        await AnalyzeRequestPatternsAsync(assessment, context);

        // Calculate overall risk score
        assessment.OverallRiskScore = CalculateRiskScore(assessment);
        assessment.ThreatLevel = DetermineThreatLevel(assessment.OverallRiskScore);

        // Handle high-risk assessments
        if (assessment.ThreatLevel >= ThreatLevel.High)
        {
            await HandleHighRiskThreatAsync(assessment);
        }

        return assessment;
    }

    private async Task HandleHighRiskThreatAsync(ThreatAssessment assessment)
    {
        // Create comprehensive security event
        var securityEvent = new SecurityEvent
        {
            EventType = SecurityEventType.HighRiskThreatDetected,
            Username = assessment.Username,
            IpAddress = assessment.IpAddress,
            ThreatLevel = assessment.ThreatLevel,
            RiskScore = assessment.OverallRiskScore,
            RiskFactors = assessment.RiskFactors,
            Timestamp = assessment.Timestamp,
            RequiresInvestigation = assessment.ThreatLevel >= ThreatLevel.Critical,
            AutomatedResponseTriggered = true
        };

        await _securityEventRepository.AddAsync(securityEvent);

        // Trigger appropriate automated responses
        await TriggerAutomatedResponseAsync(assessment);

        // Send real-time security alerts
        await SendSecurityAlertAsync(assessment);

        _logger.LogWarning("High-risk threat detected: {ThreatAssessment}", assessment);
    }

    private async Task TriggerAutomatedResponseAsync(ThreatAssessment assessment)
    {
        switch (assessment.ThreatLevel)
        {
            case ThreatLevel.Critical:
                await _incidentResponseService.InitiateCriticalIncidentResponseAsync(assessment);
                await _firewallService.BlockIpAddressAsync(assessment.IpAddress);
                await _userManagementService.LockAccountAsync(assessment.Username);
                break;

            case ThreatLevel.High:
                await _userManagementService.RequireAdditionalAuthenticationAsync(assessment.Username);
                await _monitoringService.EnableEnhancedMonitoringAsync(assessment.Username);
                break;

            case ThreatLevel.Medium:
                await _monitoringService.FlagForReviewAsync(assessment);
                break;
        }
    }
}
```

### Python/FastAPI Security Controls

**Recommended Pattern:** Comprehensive async security with advanced monitoring and data protection

```python
# Advanced Security Middleware
from fastapi import FastAPI, Request, HTTPException, status, Depends
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
from fastapi.middleware.cors import CORSMiddleware
from fastapi.middleware.trustedhost import TrustedHostMiddleware
import asyncio
import logging
from datetime import datetime, timedelta
from typing import Optional, Dict, List, Any
import jwt
import hashlib
import secrets

class ComprehensiveSecurityMiddleware:
    def __init__(self, app: FastAPI):
        self.app = app
        self.security_logger = self._setup_security_logging()
        self.threat_detector = ThreatDetectionService()
        self.data_protector = DataProtectionService()
        self.setup_middleware()

    def _setup_security_logging(self):
        logger = logging.getLogger('security')
        logger.setLevel(logging.INFO)

        # Security event handler
        security_handler = logging.FileHandler('logs/security-events.log')
        security_handler.setFormatter(logging.Formatter(
            '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
        ))

        # Audit trail handler
        audit_handler = logging.FileHandler('logs/security-audit.log')
        audit_handler.setFormatter(logging.Formatter(
            '%(asctime)s - AUDIT - %(message)s'
        ))

        logger.addHandler(security_handler)
        logger.addHandler(audit_handler)

        return logger

    def setup_middleware(self):
        # Trusted host validation
        self.app.add_middleware(
            TrustedHostMiddleware,
            allowed_hosts=["yourdomain.com", "*.yourdomain.com", "localhost"]
        )

        # CORS with strict controls
        self.app.add_middleware(
            CORSMiddleware,
            allow_origins=["https://yourdomain.com", "https://app.yourdomain.com"],
            allow_credentials=True,
            allow_methods=["GET", "POST", "PUT", "DELETE", "PATCH"],
            allow_headers=["Authorization", "Content-Type", "X-CSRF-Token", "X-Request-ID"],
            expose_headers=["X-Request-ID", "X-Rate-Limit", "X-Threat-Level"]
        )

        # Comprehensive security middleware
        @self.app.middleware("http")
        async def comprehensive_security_middleware(request: Request, call_next):
            request_id = secrets.token_hex(16)
            request.state.request_id = request_id
            start_time = datetime.utcnow()

            # Extract request information
            client_ip = self._get_client_ip(request)
            user_agent = request.headers.get("user-agent", "")

            # Initial threat assessment
            threat_assessment = await self.threat_detector.assess_request_threat(request)
            request.state.threat_assessment = threat_assessment

            # Security logging
            self.security_logger.info(
                f"[{request_id}] {request.method} {request.url} from {client_ip}",
                extra={
                    "request_id": request_id,
                    "method": request.method,
                    "url": str(request.url),
                    "client_ip": client_ip,
                    "user_agent": user_agent,
                    "threat_level": threat_assessment.risk_level.value,
                    "risk_score": threat_assessment.risk_score
                }
            )

            # Handle critical threats immediately
            if threat_assessment.risk_level == ThreatLevel.CRITICAL:
                await self._handle_critical_threat(request, threat_assessment)
                raise HTTPException(
                    status_code=status.HTTP_403_FORBIDDEN,
                    detail="Access denied due to security policy violation"
                )

            try:
                # Process request with security monitoring
                response = await call_next(request)

                # Add security headers
                self._add_security_headers(response, threat_assessment)

                # Log response
                process_time = (datetime.utcnow() - start_time).total_seconds()
                self.security_logger.info(
                    f"[{request_id}] Response {response.status_code} in {process_time:.4f}s",
                    extra={
                        "request_id": request_id,
                        "status_code": response.status_code,
                        "process_time": process_time,
                        "threat_level": threat_assessment.risk_level.value
                    }
                )

                # Post-request threat analysis
                if threat_assessment.risk_level >= ThreatLevel.HIGH:
                    await self._perform_post_request_analysis(request, response, threat_assessment)

                return response

            except Exception as e:
                # Security exception handling
                self.security_logger.error(
                    f"[{request_id}] Request processing error: {str(e)}",
                    extra={
                        "request_id": request_id,
                        "error": str(e),
                        "client_ip": client_ip,
                        "threat_level": threat_assessment.risk_level.value
                    },
                    exc_info=True
                )

                # Analyze if error might be attack-related
                if self._is_potential_attack_error(e):
                    await self._handle_potential_attack(request, e)

                raise

    def _add_security_headers(self, response, threat_assessment):
        """Add comprehensive security headers"""
        security_headers = {
            "X-Content-Type-Options": "nosniff",
            "X-Frame-Options": "DENY",
            "X-XSS-Protection": "1; mode=block",
            "Strict-Transport-Security": "max-age=31536000; includeSubDomains; preload",
            "Content-Security-Policy": (
                "default-src 'self'; "
                "script-src 'self' 'unsafe-inline' https://trusted-cdn.com; "
                "style-src 'self' 'unsafe-inline'; "
                "img-src 'self' data: https:; "
                "connect-src 'self' https://api.trusted-service.com; "
                "font-src 'self' https://fonts.gstatic.com; "
                "object-src 'none'; "
                "media-src 'self'; "
                "frame-src 'none'; "
                "base-uri 'self';"
            ),
            "Referrer-Policy": "strict-origin-when-cross-origin",
            "Permissions-Policy": "geolocation=(), microphone=(), camera=()",
            "X-Permitted-Cross-Domain-Policies": "none",
            "Cross-Origin-Embedder-Policy": "require-corp",
            "Cross-Origin-Opener-Policy": "same-origin",
            "Cross-Origin-Resource-Policy": "same-origin",
            "X-Threat-Level": threat_assessment.risk_level.value,
            "X-Request-ID": getattr(response, 'request_id', 'unknown')
        }

        for header, value in security_headers.items():
            response.headers[header] = value

class ThreatDetectionService:
    def __init__(self):
        self.ip_reputation_cache: Dict[str, Dict] = {}
        self.behavior_analytics = UserBehaviorAnalytics()
        self.threat_intelligence = ThreatIntelligenceService()

    async def assess_request_threat(self, request: Request) -> ThreatAssessment:
        """Comprehensive threat assessment for incoming requests"""
        assessment = ThreatAssessment(
            ip_address=self._get_client_ip(request),
            user_agent=request.headers.get("user-agent", ""),
            request_path=str(request.url.path),
            http_method=request.method,
            timestamp=datetime.utcnow()
        )

        # Parallel threat analysis
        await asyncio.gather(
            self._analyze_ip_reputation(assessment),
            self._analyze_request_patterns(assessment, request),
            self._analyze_user_agent(assessment),
            self._analyze_geographic_risk(assessment),
            self._analyze_request_frequency(assessment),
            self._analyze_payload_threats(assessment, request)
        )

        # Calculate risk score
        assessment.calculate_overall_risk()

        return assessment

    async def _analyze_ip_reputation(self, assessment: ThreatAssessment):
        """Analyze IP reputation using multiple threat intelligence sources"""
        try:
            ip = assessment.ip_address

            # Check cache first
            cached = self.ip_reputation_cache.get(ip)
            if cached and (datetime.utcnow() - cached['timestamp']).total_seconds() < 3600:
                reputation_data = cached['data']
            else:
                # Query multiple threat intelligence sources
                reputation_data = await self.threat_intelligence.check_ip_reputation(ip)
                self.ip_reputation_cache[ip] = {
                    'data': reputation_data,
                    'timestamp': datetime.utcnow()
                }

            # Assess reputation threats
            if reputation_data.is_malicious:
                assessment.add_risk_factor(
                    RiskFactor(
                        type="malicious_ip",
                        description=f"IP flagged as malicious: {', '.join(reputation_data.categories)}",
                        severity=RiskSeverity.CRITICAL,
                        score=75,
                        source="threat_intelligence"
                    )
                )

            if reputation_data.is_tor_exit_node:
                assessment.add_risk_factor(
                    RiskFactor(
                        type="tor_network",
                        description="Request from Tor exit node",
                        severity=RiskSeverity.HIGH,
                        score=50,
                        source="network_analysis"
                    )
                )

            if reputation_data.is_hosting_provider:
                assessment.add_risk_factor(
                    RiskFactor(
                        type="hosting_provider",
                        description="Request from hosting/cloud provider",
                        severity=RiskSeverity.MEDIUM,
                        score=25,
                        source="network_analysis"
                    )
                )

        except Exception as e:
            logging.error(f"IP reputation analysis failed for {assessment.ip_address}: {e}")

class DataProtectionService:
    def __init__(self, master_key: str):
        self.master_key = master_key.encode()
        self.key_derivation = KeyDerivationService()
        self.data_classifier = DataClassificationService()
        self.audit_logger = logging.getLogger('data_protection_audit')

    async def encrypt_sensitive_data(self, data: str, data_type: str,
                                   context: Dict[str, Any]) -> EncryptedDataResult:
        """Encrypt sensitive data with comprehensive protection and auditing"""
        try:
            # Classify data sensitivity
            classification = await self.data_classifier.classify_data(data, data_type)

            # Derive context-specific encryption key
            encryption_key = await self.key_derivation.derive_key(
                self.master_key,
                classification.sensitivity_level,
                context
            )

            # Select encryption algorithm based on classification
            algorithm = self._select_encryption_algorithm(classification)

            # Perform encryption with integrity protection
            encrypted_result = await self._perform_authenticated_encryption(
                data, encryption_key, algorithm, context
            )

            # Create audit record
            audit_record = {
                "operation": "encrypt",
                "data_type": data_type,
                "classification": classification.sensitivity_level.value,
                "context": self._sanitize_context_for_audit(context),
                "algorithm": algorithm.name,
                "timestamp": datetime.utcnow().isoformat(),
                "key_id": encryption_key.key_id
            }

            self.audit_logger.info(f"Data encryption completed: {audit_record}")

            return EncryptedDataResult(
                ciphertext=encrypted_result.ciphertext,
                key_id=encryption_key.key_id,
                algorithm=algorithm.name,
                classification=classification,
                audit_trail_id=audit_record.get("audit_id")
            )

        except Exception as e:
            self.audit_logger.error(
                f"Data encryption failed: type={data_type}, context={context}, error={str(e)}"
            )
            raise DataProtectionException("Encryption operation failed") from e

    @require_authorization("data:decrypt")
    async def decrypt_sensitive_data(self, encrypted_data: EncryptedDataResult,
                                   context: Dict[str, Any]) -> str:
        """Decrypt sensitive data with authorization and comprehensive auditing"""
        try:
            # Verify decryption authorization
            await self._verify_decryption_authorization(encrypted_data, context)

            # Get decryption key
            decryption_key = await self.key_derivation.get_key(encrypted_data.key_id)

            # Perform decryption
            decrypted_data = await self._perform_authenticated_decryption(
                encrypted_data.ciphertext,
                decryption_key,
                encrypted_data.algorithm,
                context
            )

            # Create comprehensive audit record
            audit_record = {
                "operation": "decrypt",
                "classification": encrypted_data.classification.sensitivity_level.value,
                "context": self._sanitize_context_for_audit(context),
                "user": context.get("user_id", "unknown"),
                "timestamp": datetime.utcnow().isoformat(),
                "key_id": encrypted_data.key_id,
                "justification": context.get("business_justification", "not_provided")
            }

            self.audit_logger.info(f"Data decryption completed: {audit_record}")

            return decrypted_data

        except Exception as e:
            self.audit_logger.error(
                f"Data decryption failed: key_id={encrypted_data.key_id}, "
                f"context={context}, error={str(e)}"
            )
            raise DataProtectionException("Decryption operation failed") from e
```

### Generic/Fallback Implementation

For unsupported technologies, provide generic security control patterns:

```yaml
# Generic Security Controls Configuration
security_controls:
  approach: "defense_in_depth"  # or "zero_trust", "risk_based"

  control_categories:
    - "identity_and_access_management"
    - "network_security_controls"
    - "endpoint_protection_controls"
    - "application_security_controls"
    - "data_protection_controls"
    - "monitoring_and_detection_controls"

  implementation_principles:
    - "least_privilege_access_enforcement"
    - "defense_in_depth_layered_security"
    - "continuous_monitoring_and_assessment"
    - "automated_threat_detection_and_response"
    - "comprehensive_audit_logging_and_analysis"

  technology_integration:
    - "siem_centralized_log_management"
    - "security_orchestration_automation_response"
    - "threat_intelligence_integration"
    - "vulnerability_management_automation"
    - "compliance_monitoring_and_reporting"

  operational_procedures:
    - "incident_response_and_forensics"
    - "change_management_security_reviews"
    - "access_review_and_certification"
    - "security_awareness_training_programs"
    - "continuous_improvement_and_optimization"
```

## 📊 Success Criteria

### Control Implementation Effectiveness
- **Coverage Completeness**: >95% of identified threats have corresponding controls
- **Control Operational Status**: >99% uptime for critical security controls
- **Integration Success**: 100% of security tools integrated with SIEM platform
- **Automation Level**: >80% of routine security tasks automated

### Security Posture Improvement
- **Vulnerability Reduction**: >90% reduction in critical vulnerabilities within 30 days
- **Incident Detection Speed**: Mean time to detection <5 minutes
- **Response Automation**: >70% of security incidents handled with minimal human intervention
- **Compliance Achievement**: 100% compliance with applicable regulatory frameworks

## 🎯 Deliverables

Upon completion of comprehensive security controls implementation:

- ✅ **Layered Security Architecture** with defense-in-depth controls across all technology layers
- ✅ **Identity and Access Management System** with zero trust principles and automated governance
- ✅ **Application Security Controls** integrated into development pipeline and runtime protection
- ✅ **Data Protection Framework** with classification, encryption, and privacy controls
- ✅ **Security Monitoring Platform** with advanced analytics and automated response capabilities
- ✅ **Threat Intelligence Integration** with automated IOC processing and distribution
- ✅ **Security Orchestration Playbooks** for common incident response scenarios
- ✅ **Compliance Documentation** demonstrating control implementation and effectiveness
- ✅ **Operational Procedures** for ongoing security control maintenance and optimization

## 🔄 Chatmode Transition

Security controls implementation is complete. The comprehensive security framework provides:

- **Multi-layered Defense**: Protection across all technology stack layers
- **Automated Threat Response**: Intelligent detection and response capabilities
- **Data Protection**: Comprehensive encryption and privacy controls
- **Identity Governance**: Zero trust identity and access management
- **Compliance Alignment**: Controls mapped to regulatory requirements

The security implementation is now ready for operational deployment and ongoing management. Consider regular security assessments and continuous improvement of security controls to maintain effectiveness against evolving threats.

---

*This comprehensive security controls implementation provides enterprise-grade protection while maintaining usability and enabling business functionality through systematic security engineering and automation.*