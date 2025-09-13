---
name: security-architecture-and-threat-modeling
description: Design comprehensive security architecture and conduct thorough threat modeling with technology-adaptive security patterns and frameworks
tools: [bash, glob, grep, read, edit, write, web_search, web_fetch]
model: claude-sonnet-4
---

# Security Architecture and Threat Modeling Framework

## 🎯 Mission

Design comprehensive security architecture and conduct thorough threat modeling to establish robust security controls and frameworks that protect applications, data, and infrastructure while enabling business operations and maintaining compliance requirements.

## 📋 Context-Adaptive Analysis Framework

### Initial Context Assessment

The security-engineer analyzes the copilot.instructions.md file to determine:
- **Technology Stack**: Backend framework (Java/Spring, .NET Core, Node.js, Python/FastAPI) for appropriate security implementations and vulnerability patterns
- **Database Technology**: Database system (PostgreSQL, SQL Server, MongoDB) for data protection strategies and access controls
- **Business Domain**: Industry-specific security requirements (fintech, healthcare, ecommerce) for compliance frameworks and threat landscapes
- **Project Scale**: Application complexity and user base for appropriate security controls, monitoring solutions, and risk assessment levels
- **Development Stage**: Security maturity requirements from MVP to enterprise-grade security implementations

Based on this analysis, the security engineer will select appropriate security frameworks, implement technology-specific security controls, and ensure compliance with relevant industry standards.

## 📋 Comprehensive Security Architecture Framework

### Phase 1: Security Requirements Analysis and Asset Classification

**Step 1.1: Security Requirements Analysis**

```python
# Security Requirements Assessment Framework
SECURITY_REQUIREMENTS_MATRIX = {
    'regulatory_compliance': {
        'gdpr': {
            'scope': 'european_data_subjects_personal_data',
            'key_controls': [
                'data_protection_by_design_privacy',
                'consent_management_explicit_granular',
                'data_subject_rights_automated_fulfillment',
                'breach_notification_72_hour_dpa',
                'data_protection_officer_appointment'
            ],
            'technical_requirements': [
                'pseudonymization_encryption_personal_data',
                'data_portability_machine_readable_format',
                'right_to_erasure_complete_deletion',
                'privacy_impact_assessments_high_risk'
            ]
        },
        'hipaa': {
            'scope': 'protected_health_information_phi',
            'key_controls': [
                'administrative_safeguards_workforce_training',
                'physical_safeguards_facility_access_workstation',
                'technical_safeguards_access_control_audit',
                'business_associate_agreements_third_parties'
            ],
            'technical_requirements': [
                'phi_encryption_at_rest_in_transit',
                'access_controls_minimum_necessary',
                'audit_logs_comprehensive_tamper_proof',
                'secure_backup_disaster_recovery'
            ]
        },
        'pci_dss': {
            'scope': 'cardholder_data_environment',
            'key_controls': [
                'secure_network_firewall_configuration',
                'protect_cardholder_data_encryption',
                'vulnerability_management_program',
                'access_control_need_to_know_basis',
                'network_monitoring_intrusion_detection',
                'information_security_policy'
            ],
            'technical_requirements': [
                'cardholder_data_encryption_storage_transmission',
                'secure_authentication_multi_factor',
                'network_segmentation_cardholder_data',
                'regular_security_testing_penetration'
            ]
        }
    },
    'business_risk_assessment': {
        'data_sensitivity_classification': {
            'public_data': {
                'protection_level': 'basic_integrity_availability',
                'controls': ['version_control', 'backup_procedures'],
                'encryption_required': False
            },
            'internal_data': {
                'protection_level': 'confidentiality_integrity_availability',
                'controls': ['access_control', 'audit_logging', 'data_classification'],
                'encryption_required': True
            },
            'confidential_data': {
                'protection_level': 'high_confidentiality_integrity_availability',
                'controls': ['strong_access_control', 'encryption', 'data_loss_prevention'],
                'encryption_required': True
            },
            'restricted_data': {
                'protection_level': 'maximum_confidentiality_integrity_availability',
                'controls': ['privileged_access', 'hardware_encryption', 'air_gap_isolation'],
                'encryption_required': True
            }
        },
        'threat_landscape_analysis': {
            'external_threats': [
                'nation_state_actors_apt_groups',
                'organized_cybercriminal_groups',
                'hacktivist_groups_ideological',
                'opportunistic_attackers_automated',
                'supply_chain_compromise_third_party'
            ],
            'internal_threats': [
                'malicious_insiders_privileged_access',
                'unintentional_insider_threats_human_error',
                'compromised_insider_accounts',
                'third_party_contractor_access',
                'social_engineering_internal_targets'
            ]
        }
    }
}

class SecurityRequirementsAnalyzer:
    def __init__(self, business_context, technology_stack):
        self.business_context = business_context
        self.technology_stack = technology_stack

    def analyze_security_requirements(self):
        """Comprehensive security requirements analysis"""
        requirements_analysis = {
            'regulatory_compliance_mapping': self._map_compliance_requirements(),
            'data_classification_scheme': self._classify_organizational_data(),
            'threat_landscape_assessment': self._assess_threat_landscape(),
            'business_impact_analysis': self._analyze_business_impact(),
            'security_control_requirements': self._derive_security_controls()
        }

        return requirements_analysis

    def _map_compliance_requirements(self):
        """Map business domain to applicable compliance frameworks"""
        compliance_mapping = {
            'fintech': ['pci_dss', 'gdpr', 'sox_sarbox', 'basel_iii'],
            'healthcare': ['hipaa', 'hitech', 'gdpr', 'fda_21_cfr_part_11'],
            'ecommerce': ['pci_dss', 'gdpr', 'ccpa', 'consumer_protection'],
            'government': ['fisma', 'fedramp', 'nist_800_53', 'ato_requirements'],
            'education': ['ferpa', 'coppa', 'gdpr', 'student_privacy']
        }

        applicable_frameworks = compliance_mapping.get(
            self.business_context.get('domain', 'generic'),
            ['gdpr', 'iso_27001', 'nist_cybersecurity_framework']
        )

        return applicable_frameworks

    def _classify_organizational_data(self):
        """Classify organizational data by sensitivity and criticality"""
        data_classification = {
            'customer_data': {
                'personal_identifiers': 'restricted',
                'financial_information': 'confidential',
                'contact_information': 'confidential',
                'behavioral_data': 'confidential',
                'preferences_settings': 'internal'
            },
            'business_data': {
                'intellectual_property': 'restricted',
                'financial_records': 'confidential',
                'strategic_plans': 'confidential',
                'employee_data': 'confidential',
                'vendor_contracts': 'confidential'
            },
            'operational_data': {
                'system_configurations': 'confidential',
                'security_logs': 'confidential',
                'performance_metrics': 'internal',
                'public_documentation': 'public'
            }
        }

        return data_classification
```

**Step 1.2: Asset Identification and Valuation**

```python
class SecurityAssetInventory:
    def __init__(self, technology_architecture, business_operations):
        self.architecture = technology_architecture
        self.operations = business_operations

    def create_comprehensive_asset_inventory(self):
        """Create comprehensive security asset inventory with valuation"""
        asset_inventory = {
            'information_assets': {
                'customer_data': {
                    'asset_type': 'personal_identifiable_information',
                    'business_value': 'high',
                    'confidentiality_requirement': 'high',
                    'integrity_requirement': 'high',
                    'availability_requirement': 'medium',
                    'regulatory_requirements': ['gdpr', 'ccpa', 'hipaa'],
                    'threat_exposure': 'external_internal',
                    'protection_controls': [
                        'encryption_at_rest_in_transit',
                        'access_control_rbac_abac',
                        'data_masking_tokenization',
                        'audit_logging_comprehensive'
                    ]
                },
                'intellectual_property': {
                    'asset_type': 'proprietary_business_information',
                    'business_value': 'critical',
                    'confidentiality_requirement': 'critical',
                    'integrity_requirement': 'high',
                    'availability_requirement': 'medium',
                    'regulatory_requirements': ['trade_secret_protection'],
                    'threat_exposure': 'internal_external_espionage',
                    'protection_controls': [
                        'advanced_encryption_algorithms',
                        'privileged_access_management',
                        'data_loss_prevention_dlp',
                        'information_rights_management'
                    ]
                }
            },
            'technology_assets': {
                'application_infrastructure': {
                    'web_applications': {
                        'asset_criticality': 'high',
                        'attack_surface': 'internet_facing_public',
                        'vulnerability_exposure': 'owasp_top_10',
                        'protection_requirements': [
                            'web_application_firewall',
                            'secure_coding_practices',
                            'input_validation_output_encoding',
                            'session_management_secure'
                        ]
                    },
                    'api_services': {
                        'asset_criticality': 'high',
                        'attack_surface': 'programmatic_access',
                        'vulnerability_exposure': 'api_security_top_10',
                        'protection_requirements': [
                            'api_gateway_rate_limiting',
                            'oauth2_jwt_authentication',
                            'api_versioning_deprecation',
                            'comprehensive_api_logging'
                        ]
                    },
                    'database_systems': {
                        'asset_criticality': 'critical',
                        'attack_surface': 'network_application_layer',
                        'vulnerability_exposure': 'injection_attacks',
                        'protection_requirements': [
                            'database_encryption_tde',
                            'database_access_control',
                            'database_activity_monitoring',
                            'backup_encryption_security'
                        ]
                    }
                },
                'infrastructure_components': {
                    'cloud_infrastructure': {
                        'asset_criticality': 'high',
                        'attack_surface': 'cloud_provider_shared_responsibility',
                        'vulnerability_exposure': 'misconfiguration_privilege_escalation',
                        'protection_requirements': [
                            'cloud_security_posture_management',
                            'identity_access_management_iam',
                            'network_security_groups_nacls',
                            'cloud_workload_protection'
                        ]
                    },
                    'network_infrastructure': {
                        'asset_criticality': 'high',
                        'attack_surface': 'network_perimeter_internal',
                        'vulnerability_exposure': 'lateral_movement_privilege_escalation',
                        'protection_requirements': [
                            'network_segmentation_micro',
                            'intrusion_detection_prevention',
                            'network_access_control_nac',
                            'zero_trust_network_architecture'
                        ]
                    }
                }
            },
            'human_assets': {
                'privileged_users': {
                    'administrators': {
                        'risk_level': 'critical',
                        'access_scope': 'system_wide_administrative',
                        'threat_vectors': ['insider_threat', 'account_compromise'],
                        'protection_requirements': [
                            'privileged_access_management_pam',
                            'multi_factor_authentication_hardware',
                            'session_monitoring_recording',
                            'regular_access_reviews_certification'
                        ]
                    },
                    'developers': {
                        'risk_level': 'high',
                        'access_scope': 'source_code_deployment_systems',
                        'threat_vectors': ['supply_chain_compromise', 'code_injection'],
                        'protection_requirements': [
                            'secure_development_lifecycle',
                            'code_review_security_scanning',
                            'development_environment_isolation',
                            'secrets_management_automated'
                        ]
                    }
                },
                'business_users': {
                    'data_handlers': {
                        'risk_level': 'medium',
                        'access_scope': 'business_data_customer_information',
                        'threat_vectors': ['social_engineering', 'data_exfiltration'],
                        'protection_requirements': [
                            'security_awareness_training',
                            'data_loss_prevention_endpoint',
                            'email_security_anti_phishing',
                            'incident_reporting_procedures'
                        ]
                    }
                }
            }
        }

        return asset_inventory
```

### Phase 2: Threat Modeling and Risk Assessment

**Step 2.1: STRIDE Threat Modeling Framework**

```python
class STRIDEThreatModel:
    def __init__(self, system_architecture, asset_inventory):
        self.architecture = system_architecture
        self.assets = asset_inventory

    def conduct_stride_analysis(self):
        """Comprehensive STRIDE threat modeling analysis"""
        stride_analysis = {
            'spoofing_threats': {
                'identity_spoofing': {
                    'threat_description': 'attacker_impersonates_legitimate_user_system',
                    'attack_vectors': [
                        'credential_theft_password_reuse',
                        'session_hijacking_token_theft',
                        'social_engineering_identity_theft',
                        'man_in_middle_certificate_spoofing'
                    ],
                    'affected_assets': ['user_accounts', 'authentication_systems'],
                    'business_impact': 'unauthorized_access_data_breach',
                    'likelihood': 'high',
                    'impact_severity': 'high',
                    'mitigations': [
                        'multi_factor_authentication_mandatory',
                        'certificate_pinning_validation',
                        'behavioral_authentication_biometrics',
                        'session_management_secure_tokens'
                    ]
                },
                'system_spoofing': {
                    'threat_description': 'attacker_creates_fake_system_services',
                    'attack_vectors': [
                        'dns_hijacking_domain_spoofing',
                        'rogue_access_points_wifi_evil_twin',
                        'api_endpoint_spoofing',
                        'certificate_authority_compromise'
                    ],
                    'affected_assets': ['network_infrastructure', 'client_applications'],
                    'business_impact': 'data_interception_credential_harvesting',
                    'likelihood': 'medium',
                    'impact_severity': 'high',
                    'mitigations': [
                        'certificate_transparency_monitoring',
                        'hsts_certificate_pinning',
                        'network_monitoring_anomaly_detection',
                        'secure_dns_over_https'
                    ]
                }
            },
            'tampering_threats': {
                'data_manipulation': {
                    'threat_description': 'unauthorized_modification_data_systems',
                    'attack_vectors': [
                        'sql_injection_database_manipulation',
                        'api_parameter_tampering',
                        'file_system_direct_access',
                        'memory_corruption_buffer_overflow'
                    ],
                    'affected_assets': ['database_systems', 'application_data'],
                    'business_impact': 'data_integrity_loss_financial_fraud',
                    'likelihood': 'high',
                    'impact_severity': 'critical',
                    'mitigations': [
                        'input_validation_parameterized_queries',
                        'database_integrity_constraints',
                        'file_system_permissions_access_control',
                        'code_review_static_analysis'
                    ]
                },
                'code_tampering': {
                    'threat_description': 'malicious_modification_application_code',
                    'attack_vectors': [
                        'supply_chain_compromise_dependencies',
                        'source_code_repository_compromise',
                        'build_pipeline_injection',
                        'runtime_code_injection'
                    ],
                    'affected_assets': ['source_code', 'deployment_systems'],
                    'business_impact': 'system_compromise_backdoor_installation',
                    'likelihood': 'medium',
                    'impact_severity': 'critical',
                    'mitigations': [
                        'code_signing_digital_signatures',
                        'dependency_vulnerability_scanning',
                        'build_environment_security_hardening',
                        'runtime_application_self_protection'
                    ]
                }
            },
            'repudiation_threats': {
                'action_denial': {
                    'threat_description': 'users_deny_performing_actions',
                    'attack_vectors': [
                        'log_tampering_deletion',
                        'timestamp_manipulation',
                        'non_repudiation_bypass',
                        'audit_trail_corruption'
                    ],
                    'affected_assets': ['audit_logs', 'transaction_records'],
                    'business_impact': 'legal_disputes_compliance_violations',
                    'likelihood': 'medium',
                    'impact_severity': 'medium',
                    'mitigations': [
                        'cryptographic_audit_logging',
                        'centralized_log_management_siem',
                        'digital_signatures_non_repudiation',
                        'blockchain_immutable_audit_trail'
                    ]
                }
            },
            'information_disclosure_threats': {
                'sensitive_data_exposure': {
                    'threat_description': 'unauthorized_access_sensitive_information',
                    'attack_vectors': [
                        'sql_injection_data_extraction',
                        'directory_traversal_file_disclosure',
                        'memory_dump_sensitive_data',
                        'cache_timing_side_channel'
                    ],
                    'affected_assets': ['customer_data', 'business_secrets'],
                    'business_impact': 'privacy_breach_competitive_disadvantage',
                    'likelihood': 'high',
                    'impact_severity': 'high',
                    'mitigations': [
                        'data_classification_access_control',
                        'encryption_at_rest_in_transit',
                        'data_loss_prevention_monitoring',
                        'secure_memory_management'
                    ]
                }
            },
            'denial_of_service_threats': {
                'availability_disruption': {
                    'threat_description': 'service_unavailability_performance_degradation',
                    'attack_vectors': [
                        'distributed_denial_service_ddos',
                        'application_layer_attacks',
                        'resource_exhaustion_attacks',
                        'algorithmic_complexity_attacks'
                    ],
                    'affected_assets': ['web_applications', 'api_services'],
                    'business_impact': 'service_interruption_revenue_loss',
                    'likelihood': 'high',
                    'impact_severity': 'high',
                    'mitigations': [
                        'ddos_protection_cloud_services',
                        'rate_limiting_throttling',
                        'load_balancing_auto_scaling',
                        'input_validation_complexity_limits'
                    ]
                }
            },
            'elevation_of_privilege_threats': {
                'unauthorized_privilege_escalation': {
                    'threat_description': 'gaining_higher_privileges_than_authorized',
                    'attack_vectors': [
                        'privilege_escalation_vulnerabilities',
                        'horizontal_vertical_privilege_escalation',
                        'token_manipulation_jwt_attacks',
                        'configuration_misconfiguration_abuse'
                    ],
                    'affected_assets': ['access_control_systems', 'administrative_accounts'],
                    'business_impact': 'complete_system_compromise',
                    'likelihood': 'medium',
                    'impact_severity': 'critical',
                    'mitigations': [
                        'principle_least_privilege_enforcement',
                        'regular_privilege_reviews_certification',
                        'privilege_access_management_pam',
                        'zero_trust_architecture_implementation'
                    ]
                }
            }
        }

        return stride_analysis

    def calculate_risk_scores(self, threat_analysis):
        """Calculate comprehensive risk scores for identified threats"""
        risk_matrix = {
            'probability_scale': {
                'very_low': 1,
                'low': 2,
                'medium': 3,
                'high': 4,
                'very_high': 5
            },
            'impact_scale': {
                'negligible': 1,
                'minor': 2,
                'moderate': 3,
                'major': 4,
                'catastrophic': 5
            }
        }

        risk_assessment = {}
        for threat_category, threats in threat_analysis.items():
            risk_assessment[threat_category] = {}
            for threat_name, threat_data in threats.items():
                probability_score = risk_matrix['probability_scale'].get(
                    threat_data.get('likelihood', 'medium'), 3
                )
                impact_score = risk_matrix['impact_scale'].get(
                    threat_data.get('impact_severity', 'moderate'), 3
                )
                risk_score = probability_score * impact_score

                risk_level = 'low'
                if risk_score >= 15:
                    risk_level = 'critical'
                elif risk_score >= 10:
                    risk_level = 'high'
                elif risk_score >= 6:
                    risk_level = 'medium'

                risk_assessment[threat_category][threat_name] = {
                    'probability_score': probability_score,
                    'impact_score': impact_score,
                    'risk_score': risk_score,
                    'risk_level': risk_level,
                    'priority_ranking': self._calculate_priority_ranking(
                        risk_score, threat_data
                    )
                }

        return risk_assessment
```

**Step 2.2: Attack Surface Analysis and Kill Chain Mapping**

```python
class AttackSurfaceAnalyzer:
    def __init__(self, system_architecture, network_topology):
        self.architecture = system_architecture
        self.network = network_topology

    def analyze_attack_surface(self):
        """Comprehensive attack surface analysis"""
        attack_surface_analysis = {
            'external_attack_vectors': {
                'web_application_interfaces': {
                    'entry_points': [
                        'public_web_pages_user_input',
                        'api_endpoints_rest_graphql',
                        'file_upload_functionality',
                        'search_functionality_parameters',
                        'authentication_login_forms'
                    ],
                    'attack_techniques': [
                        'injection_attacks_sql_nosql_ldap',
                        'cross_site_scripting_xss',
                        'cross_site_request_forgery_csrf',
                        'insecure_direct_object_references',
                        'security_misconfiguration_exploitation'
                    ],
                    'risk_factors': [
                        'internet_accessible_public_facing',
                        'user_generated_content_handling',
                        'third_party_integration_complexity',
                        'authentication_complexity_failure_points'
                    ]
                },
                'network_services': {
                    'exposed_services': [
                        'ssh_remote_administration',
                        'database_direct_connections',
                        'email_services_smtp_imap',
                        'dns_domain_name_resolution',
                        'monitoring_management_interfaces'
                    ],
                    'attack_techniques': [
                        'brute_force_credential_attacks',
                        'protocol_specific_vulnerabilities',
                        'man_in_middle_certificate_attacks',
                        'service_enumeration_reconnaissance',
                        'default_credential_exploitation'
                    ]
                },
                'third_party_integrations': {
                    'integration_points': [
                        'payment_processing_gateways',
                        'social_media_authentication',
                        'cloud_services_saas_integrations',
                        'supply_chain_dependencies',
                        'cdn_content_delivery_networks'
                    ],
                    'attack_techniques': [
                        'supply_chain_compromise_attacks',
                        'oauth_token_theft_manipulation',
                        'api_key_exposure_misuse',
                        'dependency_confusion_attacks',
                        'subdomain_takeover_attacks'
                    ]
                }
            },
            'internal_attack_vectors': {
                'privileged_user_access': {
                    'high_value_targets': [
                        'system_administrators_root_access',
                        'database_administrators_data_access',
                        'developers_source_code_deployment',
                        'security_personnel_monitoring_access',
                        'business_executives_sensitive_data'
                    ],
                    'attack_techniques': [
                        'credential_harvesting_keyloggers',
                        'social_engineering_spear_phishing',
                        'insider_threat_malicious_abuse',
                        'privilege_escalation_exploitation',
                        'lateral_movement_network_traversal'
                    ]
                },
                'infrastructure_components': {
                    'critical_systems': [
                        'active_directory_domain_controllers',
                        'database_servers_data_stores',
                        'application_servers_business_logic',
                        'network_infrastructure_routers_switches',
                        'backup_systems_disaster_recovery'
                    ],
                    'attack_techniques': [
                        'pass_the_hash_ticket_attacks',
                        'golden_silver_ticket_attacks',
                        'kerberoasting_asrep_roasting',
                        'network_protocol_exploitation',
                        'firmware_hardware_attacks'
                    ]
                }
            }
        }

        return attack_surface_analysis

    def map_attack_kill_chains(self):
        """Map potential attack kill chains and progression paths"""
        kill_chain_analysis = {
            'mitre_att_ck_mapping': {
                'initial_access': [
                    'spearphishing_attachment_t1566_001',
                    'exploit_public_facing_application_t1190',
                    'external_remote_services_t1133',
                    'supply_chain_compromise_t1195',
                    'valid_accounts_t1078'
                ],
                'execution': [
                    'command_scripting_interpreter_t1059',
                    'native_api_t1106',
                    'scheduled_task_job_t1053',
                    'user_execution_t1204',
                    'windows_management_instrumentation_t1047'
                ],
                'persistence': [
                    'create_modify_system_process_t1543',
                    'scheduled_task_job_t1053',
                    'boot_logon_autostart_execution_t1547',
                    'account_manipulation_t1098',
                    'hijack_execution_flow_t1574'
                ],
                'privilege_escalation': [
                    'abuse_elevation_control_mechanism_t1548',
                    'access_token_manipulation_t1134',
                    'boot_logon_initialization_scripts_t1037',
                    'exploitation_for_privilege_escalation_t1068',
                    'hijack_execution_flow_t1574'
                ],
                'defense_evasion': [
                    'obfuscated_files_information_t1027',
                    'disable_modify_security_tools_t1562',
                    'masquerading_t1036',
                    'process_injection_t1055',
                    'rootkit_t1014'
                ],
                'credential_access': [
                    'brute_force_t1110',
                    'credential_dumping_t1003',
                    'input_capture_t1056',
                    'kerberoasting_t1558_003',
                    'steal_web_session_cookie_t1539'
                ],
                'discovery': [
                    'account_discovery_t1087',
                    'network_service_scanning_t1046',
                    'permission_groups_discovery_t1069',
                    'remote_system_discovery_t1018',
                    'system_information_discovery_t1082'
                ],
                'lateral_movement': [
                    'exploitation_of_remote_services_t1210',
                    'internal_spearphishing_t1534',
                    'remote_services_t1021',
                    'taint_shared_content_t1080',
                    'use_alternate_authentication_material_t1550'
                ],
                'collection': [
                    'automated_collection_t1119',
                    'clipboard_data_t1115',
                    'data_from_information_repositories_t1213',
                    'input_capture_t1056',
                    'screen_capture_t1113'
                ],
                'exfiltration': [
                    'automated_exfiltration_t1020',
                    'data_transfer_size_limits_t1030',
                    'exfiltration_over_c2_channel_t1041',
                    'exfiltration_over_web_service_t1567',
                    'scheduled_transfer_t1029'
                ]
            },
            'attack_progression_scenarios': {
                'external_web_compromise': [
                    'reconnaissance_osint_gathering',
                    'vulnerability_scanning_exploitation',
                    'web_shell_deployment_persistence',
                    'privilege_escalation_system_compromise',
                    'lateral_movement_network_traversal',
                    'data_exfiltration_mission_completion'
                ],
                'insider_threat_scenario': [
                    'legitimate_access_credential_abuse',
                    'privilege_escalation_administrative_access',
                    'data_access_sensitive_information',
                    'data_collection_unauthorized_copying',
                    'exfiltration_covert_channels',
                    'evidence_destruction_log_tampering'
                ]
            }
        }

        return kill_chain_analysis
```

### Phase 3: Security Controls Design and Implementation

**Step 3.1: Defense-in-Depth Security Architecture**

```python
class DefenseInDepthArchitecture:
    def __init__(self, threat_model, business_requirements):
        self.threats = threat_model
        self.requirements = business_requirements

    def design_layered_security_controls(self):
        """Design comprehensive layered security controls"""
        layered_security = {
            'perimeter_security_layer': {
                'network_perimeter_controls': {
                    'next_generation_firewalls': {
                        'capabilities': [
                            'application_layer_inspection',
                            'intrusion_prevention_system',
                            'ssl_tls_inspection_decryption',
                            'threat_intelligence_integration',
                            'geo_location_blocking'
                        ],
                        'deployment_patterns': [
                            'dmz_network_segmentation',
                            'internal_network_microsegmentation',
                            'cloud_native_firewall_rules',
                            'zero_trust_network_access'
                        ]
                    },
                    'web_application_firewalls': {
                        'protection_capabilities': [
                            'owasp_top_10_protection',
                            'bot_detection_mitigation',
                            'rate_limiting_ddos_protection',
                            'api_security_gateway',
                            'custom_rule_development'
                        ],
                        'deployment_models': [
                            'cloud_based_waf_service',
                            'on_premise_appliance',
                            'hybrid_deployment_model',
                            'cdn_integrated_protection'
                        ]
                    }
                },
                'email_security_gateway': {
                    'threat_protection': [
                        'advanced_threat_protection_atp',
                        'phishing_simulation_training',
                        'business_email_compromise_protection',
                        'data_loss_prevention_email',
                        'encryption_digital_signatures'
                    ]
                }
            },
            'network_security_layer': {
                'network_segmentation': {
                    'macro_segmentation': {
                        'implementation': 'vlan_based_network_separation',
                        'segments': [
                            'dmz_public_facing_services',
                            'application_tier_business_logic',
                            'database_tier_data_storage',
                            'management_network_administration',
                            'user_network_workstations'
                        ]
                    },
                    'micro_segmentation': {
                        'implementation': 'software_defined_networking_sdn',
                        'granularity': 'application_workload_level',
                        'policies': [
                            'zero_trust_default_deny',
                            'least_privilege_network_access',
                            'east_west_traffic_inspection',
                            'behavioral_anomaly_detection'
                        ]
                    }
                },
                'network_monitoring': {
                    'network_detection_response': {
                        'capabilities': [
                            'network_traffic_analysis_nta',
                            'behavioral_analytics_machine_learning',
                            'threat_hunting_capabilities',
                            'incident_response_orchestration',
                            'forensic_pcap_analysis'
                        ]
                    }
                }
            },
            'endpoint_security_layer': {
                'endpoint_detection_response': {
                    'protection_capabilities': [
                        'real_time_threat_detection',
                        'behavioral_analysis_heuristics',
                        'memory_protection_exploit_prevention',
                        'fileless_attack_detection',
                        'threat_intelligence_correlation'
                    ],
                    'response_capabilities': [
                        'automated_threat_containment',
                        'forensic_evidence_collection',
                        'remote_remediation_capabilities',
                        'incident_response_integration',
                        'threat_hunting_tools'
                    ]
                },
                'mobile_device_management': {
                    'byod_security_controls': [
                        'device_compliance_enforcement',
                        'application_management_security',
                        'data_segregation_containerization',
                        'remote_wipe_capabilities',
                        'certificate_based_authentication'
                    ]
                }
            },
            'application_security_layer': {
                'secure_development_lifecycle': {
                    'security_by_design': [
                        'threat_modeling_design_phase',
                        'secure_coding_standards_training',
                        'static_dynamic_security_testing',
                        'dependency_vulnerability_scanning',
                        'security_code_review_process'
                    ]
                },
                'runtime_application_protection': {
                    'protection_mechanisms': [
                        'input_validation_sanitization',
                        'output_encoding_xss_prevention',
                        'sql_injection_prevention',
                        'csrf_protection_tokens',
                        'session_management_security'
                    ]
                }
            },
            'data_security_layer': {
                'data_classification_protection': {
                    'classification_scheme': [
                        'public_unrestricted_data',
                        'internal_business_sensitive',
                        'confidential_competitive_advantage',
                        'restricted_regulated_data'
                    ],
                    'protection_controls': [
                        'encryption_at_rest_in_transit',
                        'data_loss_prevention_monitoring',
                        'access_control_attribute_based',
                        'data_masking_tokenization',
                        'rights_management_digital_protection'
                    ]
                },
                'database_security': {
                    'protection_mechanisms': [
                        'transparent_data_encryption_tde',
                        'database_activity_monitoring_dam',
                        'privileged_user_monitoring',
                        'dynamic_data_masking',
                        'database_firewall_protection'
                    ]
                }
            },
            'identity_access_management_layer': {
                'identity_governance': {
                    'access_lifecycle_management': [
                        'automated_provisioning_deprovisioning',
                        'role_based_access_control_rbac',
                        'attribute_based_access_control_abac',
                        'periodic_access_certification',
                        'segregation_duties_enforcement'
                    ]
                },
                'privileged_access_management': {
                    'pam_capabilities': [
                        'privileged_account_discovery',
                        'password_vaulting_rotation',
                        'session_monitoring_recording',
                        'just_in_time_access',
                        'privileged_threat_analytics'
                    ]
                }
            }
        }

        return layered_security
```

**Step 3.2: Zero Trust Architecture Implementation**

```python
class ZeroTrustArchitectureFramework:
    def __init__(self, organization_assets, threat_landscape):
        self.assets = organization_assets
        self.threats = threat_landscape

    def implement_zero_trust_principles(self):
        """Implement comprehensive zero trust architecture"""
        zero_trust_implementation = {
            'core_principles': {
                'never_trust_always_verify': {
                    'implementation_approach': 'continuous_verification_all_interactions',
                    'verification_mechanisms': [
                        'multi_factor_authentication_continuous',
                        'device_health_attestation',
                        'behavioral_analytics_risk_scoring',
                        'contextual_access_decisions',
                        'real_time_threat_intelligence'
                    ]
                },
                'least_privilege_access': {
                    'implementation_approach': 'minimal_access_rights_granted',
                    'access_control_mechanisms': [
                        'just_in_time_access_provisioning',
                        'just_enough_access_scope_limitation',
                        'dynamic_access_evaluation',
                        'session_based_access_controls',
                        'automated_access_revocation'
                    ]
                },
                'assume_breach_mentality': {
                    'implementation_approach': 'continuous_monitoring_threat_detection',
                    'detection_response_capabilities': [
                        'lateral_movement_detection',
                        'anomaly_detection_machine_learning',
                        'threat_hunting_proactive',
                        'incident_response_automation',
                        'forensic_evidence_preservation'
                    ]
                }
            },
            'zero_trust_architecture_components': {
                'identity_verification_engine': {
                    'capabilities': [
                        'adaptive_authentication_risk_based',
                        'continuous_user_verification',
                        'device_trust_assessment',
                        'behavioral_biometrics_analysis',
                        'threat_intelligence_integration'
                    ],
                    'integration_points': [
                        'identity_providers_federation',
                        'privileged_access_management',
                        'single_sign_on_solutions',
                        'certificate_authorities',
                        'hardware_security_modules'
                    ]
                },
                'policy_decision_engine': {
                    'policy_evaluation_factors': [
                        'user_identity_attributes',
                        'device_security_posture',
                        'network_location_context',
                        'application_sensitivity_level',
                        'real_time_risk_assessment'
                    ],
                    'policy_enforcement_mechanisms': [
                        'software_defined_perimeter',
                        'network_access_control',
                        'application_proxy_gateways',
                        'api_security_gateways',
                        'cloud_access_security_brokers'
                    ]
                },
                'micro_segmentation_fabric': {
                    'segmentation_granularity': [
                        'application_workload_isolation',
                        'user_group_network_separation',
                        'device_type_access_zones',
                        'data_classification_boundaries',
                        'geographical_location_controls'
                    ],
                    'enforcement_mechanisms': [
                        'software_defined_networking',
                        'container_network_policies',
                        'cloud_native_security_groups',
                        'endpoint_firewall_rules',
                        'application_layer_controls'
                    ]
                }
            }
        }

        return zero_trust_implementation
```

## 🔧 Technology-Adaptive Implementation

### Java/Spring Boot Security Architecture

**Recommended Pattern:** Enterprise security with comprehensive threat protection and monitoring

```java
// Comprehensive Security Configuration
@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true, securedEnabled = true)
public class EnterpriseSecurityConfiguration {

    @Autowired
    private ThreatDetectionService threatDetectionService;

    @Autowired
    private DataProtectionService dataProtectionService;

    @Bean
    public SecurityFilterChain enterpriseSecurityFilterChain(HttpSecurity http) throws Exception {
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
        http.addFilterAfter(new SecurityAuditFilter(), SecurityContextPersistenceFilter.class);

        return http.build();
    }

    @Bean
    public PasswordEncoder enterprisePasswordEncoder() {
        return new BCryptPasswordEncoder(12);
    }
}

// Advanced Threat Detection Service
@Service
@Transactional
public class AdvancedThreatDetectionService {

    private static final Logger logger = LoggerFactory.getLogger(AdvancedThreatDetectionService.class);

    @Autowired
    private SecurityEventRepository securityEventRepository;

    @Autowired
    private ThreatIntelligenceService threatIntelligenceService;

    @Autowired
    private UserBehaviorAnalyticsService userBehaviorService;

    public ThreatAssessment assessRequestThreat(HttpServletRequest request, String username) {
        ThreatAssessment assessment = new ThreatAssessment();
        assessment.setUsername(username);
        assessment.setIpAddress(getClientIpAddress(request));
        assessment.setUserAgent(request.getHeader("User-Agent"));
        assessment.setTimestamp(Instant.now());

        // Multi-dimensional threat analysis
        assessment.setRiskScore(0);

        // IP reputation analysis
        IpReputationAnalysis ipAnalysis = threatIntelligenceService.analyzeIpReputation(
            assessment.getIpAddress()
        );
        if (ipAnalysis.isMalicious()) {
            assessment.incrementRiskScore(50);
            assessment.addThreatIndicator("MALICIOUS_IP", ipAnalysis.getThreatCategories());
        }

        // User behavior analysis
        BehavioralRiskAssessment behaviorAnalysis = userBehaviorService.assessUserBehavior(
            username, request
        );
        if (behaviorAnalysis.isAnomalous()) {
            assessment.incrementRiskScore(behaviorAnalysis.getRiskContribution());
            assessment.addThreatIndicator("ANOMALOUS_BEHAVIOR", behaviorAnalysis.getAnomalies());
        }

        // Request pattern analysis
        RequestPatternAnalysis requestAnalysis = analyzeRequestPatterns(request);
        if (requestAnalysis.isSuspicious()) {
            assessment.incrementRiskScore(requestAnalysis.getRiskScore());
            assessment.addThreatIndicator("SUSPICIOUS_REQUEST", requestAnalysis.getSuspiciousPatterns());
        }

        // Geolocation risk analysis
        GeolocationRiskAnalysis geoAnalysis = analyzeGeolocationRisk(username,
            assessment.getIpAddress());
        if (geoAnalysis.isHighRisk()) {
            assessment.incrementRiskScore(geoAnalysis.getRiskScore());
            assessment.addThreatIndicator("HIGH_RISK_LOCATION", geoAnalysis.getRiskFactors());
        }

        // Determine overall threat level
        assessment.setThreatLevel(determineThreatLevel(assessment.getRiskScore()));

        // Log and respond to high-risk assessments
        if (assessment.getThreatLevel().ordinal() >= ThreatLevel.HIGH.ordinal()) {
            logHighRiskAssessment(assessment);
            triggerSecurityResponse(assessment);
        }

        return assessment;
    }

    private void logHighRiskAssessment(ThreatAssessment assessment) {
        SecurityEvent securityEvent = SecurityEvent.builder()
            .eventType(SecurityEventType.HIGH_RISK_ACCESS_ATTEMPT)
            .username(assessment.getUsername())
            .ipAddress(assessment.getIpAddress())
            .riskScore(assessment.getRiskScore())
            .threatIndicators(assessment.getThreatIndicators())
            .timestamp(assessment.getTimestamp())
            .build();

        securityEventRepository.save(securityEvent);

        logger.warn("High-risk access attempt detected: User={}, IP={}, RiskScore={}, Indicators={}",
            assessment.getUsername(),
            assessment.getIpAddress(),
            assessment.getRiskScore(),
            assessment.getThreatIndicators()
        );
    }

    private void triggerSecurityResponse(ThreatAssessment assessment) {
        switch (assessment.getThreatLevel()) {
            case CRITICAL:
                // Immediate account suspension and security team alert
                suspendUserAccount(assessment.getUsername());
                sendImmediateSecurityAlert(assessment);
                break;
            case HIGH:
                // Require additional authentication
                requireStepUpAuthentication(assessment.getUsername());
                sendSecurityAlert(assessment);
                break;
            case MEDIUM:
                // Enhanced monitoring
                enableEnhancedMonitoring(assessment.getUsername());
                break;
        }
    }
}

// Data Protection and Encryption Service
@Service
public class EnterpriseDataProtectionService {

    private static final Logger logger = LoggerFactory.getLogger(EnterpriseDataProtectionService.class);

    @Autowired
    private KeyManagementService keyManagementService;

    @Autowired
    private DataClassificationService dataClassificationService;

    @Autowired
    private AuditService auditService;

    @PreAuthorize("hasPermission(#dataType, 'ENCRYPT')")
    public EncryptedData encryptSensitiveData(String plaintext, DataType dataType,
                                             EncryptionContext context) {
        try {
            // Classify data sensitivity
            DataClassification classification = dataClassificationService.classify(plaintext, dataType);

            // Select encryption strength based on classification
            EncryptionAlgorithm algorithm = selectEncryptionAlgorithm(classification);

            // Get appropriate encryption key
            EncryptionKey key = keyManagementService.getEncryptionKey(
                dataType, classification, context
            );

            // Perform encryption with authenticated encryption
            byte[] encrypted = performAuthenticatedEncryption(plaintext.getBytes(), key, algorithm);

            // Create encrypted data object
            EncryptedData encryptedData = EncryptedData.builder()
                .ciphertext(Base64.getEncoder().encodeToString(encrypted))
                .algorithm(algorithm.getName())
                .keyId(key.getKeyId())
                .dataClassification(classification)
                .encryptionTimestamp(Instant.now())
                .context(context)
                .build();

            // Audit encryption operation
            auditService.logDataEncryption(dataType, classification, context,
                getCurrentUser().getUsername());

            logger.info("Data encrypted successfully: Type={}, Classification={}, KeyId={}",
                dataType, classification, key.getKeyId());

            return encryptedData;

        } catch (Exception e) {
            logger.error("Data encryption failed: Type={}, Context={}", dataType, context, e);
            throw new DataProtectionException("Encryption operation failed", e);
        }
    }

    @PreAuthorize("hasPermission(#encryptedData.dataClassification, 'DECRYPT')")
    public String decryptSensitiveData(EncryptedData encryptedData, EncryptionContext context) {
        try {
            // Verify decryption authorization
            verifyDecryptionAuthorization(encryptedData, context);

            // Get decryption key
            EncryptionKey key = keyManagementService.getDecryptionKey(encryptedData.getKeyId());

            // Perform decryption
            byte[] decrypted = performAuthenticatedDecryption(
                Base64.getDecoder().decode(encryptedData.getCiphertext()),
                key,
                EncryptionAlgorithm.fromName(encryptedData.getAlgorithm())
            );

            String plaintext = new String(decrypted, StandardCharsets.UTF_8);

            // Audit decryption operation
            auditService.logDataDecryption(encryptedData.getDataClassification(), context,
                getCurrentUser().getUsername());

            logger.info("Data decrypted successfully: Classification={}, KeyId={}",
                encryptedData.getDataClassification(), encryptedData.getKeyId());

            return plaintext;

        } catch (Exception e) {
            logger.error("Data decryption failed: KeyId={}, Context={}",
                encryptedData.getKeyId(), context, e);
            throw new DataProtectionException("Decryption operation failed", e);
        }
    }
}
```

### .NET Core Security Architecture

**Recommended Pattern:** Enterprise security with comprehensive identity management and protection

```csharp
// Enterprise Security Configuration
public class EnterpriseSecurityConfiguration
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Advanced Identity Configuration
        services.AddIdentity<ApplicationUser, ApplicationRole>(options =>
        {
            // Password policy - enterprise grade
            options.Password.RequiredLength = 14;
            options.Password.RequireDigit = true;
            options.Password.RequireUppercase = true;
            options.Password.RequireLowercase = true;
            options.Password.RequireNonAlphanumeric = true;
            options.Password.RequiredUniqueChars = 6;

            // Lockout policy - progressive lockout
            options.Lockout.MaxFailedAccessAttempts = 3;
            options.Lockout.DefaultLockoutTimeSpan = TimeSpan.FromMinutes(30);
            options.Lockout.AllowedForNewUsers = true;

            // User validation
            options.User.RequireUniqueEmail = true;
            options.SignIn.RequireConfirmedEmail = true;
            options.SignIn.RequireConfirmedAccount = true;
        })
        .AddEntityFrameworkStores<SecurityDbContext>()
        .AddDefaultTokenProviders()
        .AddPasswordValidator<EnterprisePasswordValidator<ApplicationUser>>();

        // JWT with advanced security
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
                RequireSignedTokens = true,
                RoleClaimType = ClaimTypes.Role,
                NameClaimType = ClaimTypes.NameIdentifier
            };

            options.Events = new JwtBearerEvents
            {
                OnAuthenticationFailed = async context =>
                {
                    var threatDetection = context.HttpContext.RequestServices
                        .GetRequiredService<IThreatDetectionService>();
                    await threatDetection.HandleAuthenticationFailureAsync(context);
                },
                OnTokenValidated = async context =>
                {
                    var securityAudit = context.HttpContext.RequestServices
                        .GetRequiredService<ISecurityAuditService>();
                    await securityAudit.LogSuccessfulAuthenticationAsync(context);
                }
            };
        });

        // Comprehensive Authorization Policies
        services.AddAuthorization(options =>
        {
            // Role-based policies
            options.AddPolicy("RequireAdministratorRole", policy =>
                policy.RequireRole("Administrator"));

            options.AddPolicy("RequireManagerRole", policy =>
                policy.RequireRole("Manager", "Administrator"));

            // Claim-based policies
            options.AddPolicy("RequireHighClearance", policy =>
                policy.RequireClaim("SecurityClearance", "High", "Critical"));

            options.AddPolicy("RequirePIIAccess", policy =>
                policy.RequireClaim("DataAccess", "PII"));

            // Custom requirement policies
            options.AddPolicy("RequireDataClassificationAccess", policy =>
                policy.Requirements.Add(new DataClassificationRequirement()));

            options.AddPolicy("RequireGeographicAccess", policy =>
                policy.Requirements.Add(new GeographicAccessRequirement()));

            options.AddPolicy("RequireThreatAssessment", policy =>
                policy.Requirements.Add(new ThreatAssessmentRequirement()));
        });

        // Security services
        services.AddScoped<IThreatDetectionService, AdvancedThreatDetectionService>();
        services.AddScoped<IDataProtectionService, EnterpriseDataProtectionService>();
        services.AddScoped<ISecurityAuditService, ComprehensiveSecurityAuditService>();
        services.AddScoped<IUserBehaviorAnalyticsService, UserBehaviorAnalyticsService>();
        services.AddScoped<IThreatIntelligenceService, ThreatIntelligenceService>();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        // Security headers middleware
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

        // Custom security middleware
        app.UseMiddleware<ThreatDetectionMiddleware>();
        app.UseMiddleware<DataProtectionMiddleware>();
        app.UseMiddleware<SecurityAuditMiddleware>();
        app.UseMiddleware<RateLimitingMiddleware>();

        app.UseAuthentication();
        app.UseAuthorization();
    }
}

// Advanced Threat Detection Service
public interface IThreatDetectionService
{
    Task<ThreatAssessment> AssessRequestThreatAsync(HttpContext context, string username);
    Task HandleAuthenticationFailureAsync(AuthenticationFailedContext context);
    Task<bool> IsHighRiskRequestAsync(HttpContext context);
}

public class AdvancedThreatDetectionService : IThreatDetectionService
{
    private readonly ILogger<AdvancedThreatDetectionService> _logger;
    private readonly IThreatIntelligenceService _threatIntelligence;
    private readonly IUserBehaviorAnalyticsService _behaviorAnalytics;
    private readonly ISecurityEventRepository _securityEventRepository;
    private readonly IConfiguration _configuration;

    public async Task<ThreatAssessment> AssessRequestThreatAsync(HttpContext context, string username)
    {
        var assessment = new ThreatAssessment
        {
            Username = username,
            IpAddress = GetClientIpAddress(context),
            UserAgent = context.Request.Headers["User-Agent"].ToString(),
            Timestamp = DateTime.UtcNow,
            RequestPath = context.Request.Path,
            HttpMethod = context.Request.Method
        };

        // Multi-factor threat analysis
        await AnalyzeIpReputationAsync(assessment);
        await AnalyzeUserBehaviorAsync(assessment, context);
        await AnalyzeRequestPatternsAsync(assessment, context);
        await AnalyzeGeolocationRiskAsync(assessment);
        await AnalyzeDeviceFingerprint(assessment, context);

        // Calculate overall risk score
        assessment.OverallRiskScore = CalculateOverallRiskScore(assessment);
        assessment.ThreatLevel = DetermineThreatLevel(assessment.OverallRiskScore);

        // Handle high-risk assessments
        if (assessment.ThreatLevel >= ThreatLevel.High)
        {
            await HandleHighRiskAssessmentAsync(assessment);
        }

        // Log assessment
        await LogThreatAssessmentAsync(assessment);

        return assessment;
    }

    private async Task AnalyzeIpReputationAsync(ThreatAssessment assessment)
    {
        var ipAnalysis = await _threatIntelligence.AnalyzeIpReputationAsync(assessment.IpAddress);

        if (ipAnalysis.IsMalicious)
        {
            assessment.RiskFactors.Add(new RiskFactor
            {
                Type = "MaliciousIP",
                Severity = ipAnalysis.Severity,
                Description = $"IP reputation indicates malicious activity: {string.Join(", ", ipAnalysis.ThreatCategories)}",
                RiskScore = 75
            });
        }

        if (ipAnalysis.IsFromTorNetwork)
        {
            assessment.RiskFactors.Add(new RiskFactor
            {
                Type = "TorNetwork",
                Severity = RiskSeverity.Medium,
                Description = "Request originated from Tor network",
                RiskScore = 40
            });
        }

        if (ipAnalysis.IsFromVpn && !IsVpnAllowed(assessment.Username))
        {
            assessment.RiskFactors.Add(new RiskFactor
            {
                Type = "UnauthorizedVPN",
                Severity = RiskSeverity.Medium,
                Description = "Request from VPN service without authorization",
                RiskScore = 30
            });
        }
    }

    private async Task HandleHighRiskAssessmentAsync(ThreatAssessment assessment)
    {
        // Create security event
        var securityEvent = new SecurityEvent
        {
            EventType = SecurityEventType.HighRiskAccessAttempt,
            Username = assessment.Username,
            IpAddress = assessment.IpAddress,
            RiskScore = assessment.OverallRiskScore,
            ThreatLevel = assessment.ThreatLevel,
            RiskFactors = assessment.RiskFactors,
            Timestamp = assessment.Timestamp,
            RequiresInvestigation = assessment.ThreatLevel >= ThreatLevel.Critical
        };

        await _securityEventRepository.AddAsync(securityEvent);

        // Trigger appropriate responses
        switch (assessment.ThreatLevel)
        {
            case ThreatLevel.Critical:
                await TriggerCriticalThreatResponseAsync(assessment);
                break;
            case ThreatLevel.High:
                await TriggerHighThreatResponseAsync(assessment);
                break;
        }

        _logger.LogWarning("High-risk access attempt: User={Username}, IP={IpAddress}, RiskScore={RiskScore}, Factors={@RiskFactors}",
            assessment.Username, assessment.IpAddress, assessment.OverallRiskScore, assessment.RiskFactors);
    }
}
```

### Node.js/Express Security Architecture

**Recommended Pattern:** Comprehensive middleware-based security with advanced threat detection

```javascript
// Advanced Security Configuration
const express = require('express');
const helmet = require('helmet');
const rateLimit = require('express-rate-limit');
const slowDown = require('express-slow-down');
const passport = require('passport');
const JwtStrategy = require('passport-jwt').Strategy;
const ExtractJwt = require('passport-jwt').ExtractJwt;
const winston = require('winston');
const cors = require('cors');

class EnterpriseSecurityConfiguration {
    constructor(app) {
        this.app = app;
        this.setupLogging();
        this.setupSecurityMiddleware();
        this.setupAdvancedRateLimiting();
        this.setupAuthentication();
        this.setupThreatDetection();
    }

    setupLogging() {
        this.securityLogger = winston.createLogger({
            level: 'info',
            format: winston.format.combine(
                winston.format.timestamp(),
                winston.format.errors({ stack: true }),
                winston.format.json()
            ),
            transports: [
                new winston.transports.File({
                    filename: 'logs/security-error.log',
                    level: 'error'
                }),
                new winston.transports.File({
                    filename: 'logs/security-combined.log'
                }),
                new winston.transports.Console({
                    format: winston.format.simple()
                })
            ]
        });
    }

    setupSecurityMiddleware() {
        // Advanced helmet configuration
        this.app.use(helmet({
            contentSecurityPolicy: {
                directives: {
                    defaultSrc: ["'self'"],
                    scriptSrc: ["'self'", "'unsafe-inline'", 'https://trusted-scripts.com'],
                    styleSrc: ["'self'", "'unsafe-inline'", 'https://fonts.googleapis.com'],
                    fontSrc: ["'self'", 'https://fonts.gstatic.com'],
                    imgSrc: ["'self'", 'data:', 'https:'],
                    connectSrc: ["'self'", 'https://api.trusted-service.com'],
                    frameSrc: ["'none'"],
                    objectSrc: ["'none'"],
                    mediaSrc: ["'self'"],
                    manifestSrc: ["'self'"],
                    workerSrc: ["'self'"]
                },
                reportOnly: false
            },
            hsts: {
                maxAge: 31536000,
                includeSubDomains: true,
                preload: true
            },
            noSniff: true,
            frameguard: { action: 'deny' },
            xssFilter: true
        }));

        // CORS configuration
        this.app.use(cors({
            origin: function (origin, callback) {
                const allowedOrigins = process.env.ALLOWED_ORIGINS?.split(',') || ['http://localhost:3000'];
                if (!origin) return callback(null, true);
                if (allowedOrigins.indexOf(origin) !== -1) {
                    callback(null, true);
                } else {
                    callback(new Error('Not allowed by CORS'));
                }
            },
            credentials: true,
            optionsSuccessStatus: 200,
            methods: ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
            allowedHeaders: ['Content-Type', 'Authorization', 'X-Requested-With']
        }));

        // Security headers middleware
        this.app.use((req, res, next) => {
            res.setHeader('X-Content-Type-Options', 'nosniff');
            res.setHeader('X-Frame-Options', 'DENY');
            res.setHeader('X-XSS-Protection', '1; mode=block');
            res.setHeader('Referrer-Policy', 'strict-origin-when-cross-origin');
            res.setHeader('Permissions-Policy', 'geolocation=(), microphone=(), camera=()');
            next();
        });

        // Request logging and monitoring
        this.app.use((req, res, next) => {
            const startTime = Date.now();
            const requestData = {
                method: req.method,
                url: req.url,
                ip: req.ip,
                userAgent: req.get('User-Agent'),
                timestamp: new Date().toISOString(),
                headers: this.sanitizeHeaders(req.headers)
            };

            // Log request
            this.securityLogger.info('Incoming request', requestData);

            // Check for suspicious patterns
            if (this.isSuspiciousRequest(req)) {
                this.securityLogger.warn('Suspicious request detected', {
                    ...requestData,
                    suspiciousPatterns: this.identifySuspiciousPatterns(req)
                });
                // Continue processing but flag for monitoring
                req.isSuspicious = true;
            }

            // Response time monitoring
            res.on('finish', () => {
                const duration = Date.now() - startTime;
                this.securityLogger.info('Request completed', {
                    ...requestData,
                    statusCode: res.statusCode,
                    duration,
                    contentLength: res.get('Content-Length')
                });
            });

            next();
        });
    }

    setupAdvancedRateLimiting() {
        // Progressive delay for suspicious requests
        const speedLimiter = slowDown({
            windowMs: 15 * 60 * 1000, // 15 minutes
            delayAfter: 2, // allow 2 requests per windowMs without delay
            delayMs: 500, // add 500ms delay per request after delayAfter
            maxDelayMs: 20000, // maximum delay of 20 seconds
            onLimitReached: (req, res, options) => {
                this.securityLogger.warn('Speed limit reached', {
                    ip: req.ip,
                    userAgent: req.get('User-Agent'),
                    url: req.url
                });
            }
        });

        // General rate limiting
        const generalLimiter = rateLimit({
            windowMs: 15 * 60 * 1000, // 15 minutes
            max: 1000, // limit each IP to 1000 requests per windowMs
            standardHeaders: true,
            legacyHeaders: false,
            handler: (req, res) => {
                this.securityLogger.error('Rate limit exceeded', {
                    ip: req.ip,
                    userAgent: req.get('User-Agent'),
                    url: req.url,
                    timestamp: new Date().toISOString()
                });
                res.status(429).json({
                    error: 'Too many requests',
                    retryAfter: Math.round(req.rateLimit.resetTime / 1000)
                });
            },
            skip: (req) => {
                return this.isWhitelistedIP(req.ip);
            }
        });

        // Strict rate limiting for authentication
        const authLimiter = rateLimit({
            windowMs: 5 * 60 * 1000, // 5 minutes
            max: 5, // limit each IP to 5 auth requests per windowMs
            skipSuccessfulRequests: true,
            handler: (req, res) => {
                this.securityLogger.error('Authentication rate limit exceeded', {
                    ip: req.ip,
                    userAgent: req.get('User-Agent'),
                    timestamp: new Date().toISOString()
                });
                res.status(429).json({
                    error: 'Too many authentication attempts',
                    lockoutDuration: 300 // 5 minutes
                });
            }
        });

        // Apply rate limiters
        this.app.use(speedLimiter);
        this.app.use('/api/', generalLimiter);
        this.app.use('/api/auth/', authLimiter);
    }

    setupThreatDetection() {
        this.threatDetection = new AdvancedThreatDetectionService();

        this.app.use(async (req, res, next) => {
            try {
                const threatAssessment = await this.threatDetection.assessRequest(req);

                if (threatAssessment.riskLevel === 'CRITICAL') {
                    this.securityLogger.error('Critical threat detected', {
                        ip: req.ip,
                        threatAssessment,
                        timestamp: new Date().toISOString()
                    });

                    return res.status(403).json({
                        error: 'Access denied due to security policy',
                        requestId: req.id
                    });
                }

                if (threatAssessment.riskLevel === 'HIGH') {
                    req.requiresAdditionalAuth = true;
                }

                req.threatAssessment = threatAssessment;
                next();

            } catch (error) {
                this.securityLogger.error('Threat detection error', {
                    error: error.message,
                    stack: error.stack,
                    ip: req.ip,
                    timestamp: new Date().toISOString()
                });
                next(); // Continue processing on threat detection failure
            }
        });
    }

    isSuspiciousRequest(req) {
        const suspiciousPatterns = [
            /\.\.[\/\\]/,     // Directory traversal
            /<script[^>]*>.*?<\/script>/gi, // XSS patterns
            /union.*select/gi, // SQL injection
            /eval\s*\(/gi,     // Code injection
            /\bor\s+1\s*=\s*1/gi, // SQL injection
            /javascript:/gi,   // JavaScript protocol
            /<iframe/gi,       // Iframe injection
            /data:text\/html/gi // Data URI XSS
        ];

        const testString = `${req.url} ${JSON.stringify(req.query)} ${JSON.stringify(req.body)}`;
        return suspiciousPatterns.some(pattern => pattern.test(testString));
    }

    identifySuspiciousPatterns(req) {
        const patterns = [];
        const testString = `${req.url} ${JSON.stringify(req.query)} ${JSON.stringify(req.body)}`;

        if (/\.\.[\/\\]/.test(testString)) patterns.push('directory_traversal');
        if (/<script[^>]*>.*?<\/script>/gi.test(testString)) patterns.push('xss_attempt');
        if (/union.*select/gi.test(testString)) patterns.push('sql_injection');
        if (/eval\s*\(/gi.test(testString)) patterns.push('code_injection');

        return patterns;
    }
}

// Advanced Threat Detection Service
class AdvancedThreatDetectionService {
    constructor() {
        this.ipReputationCache = new Map();
        this.behaviorBaseline = new Map();
        this.suspiciousIPs = new Set();
        this.logger = winston.createLogger({
            level: 'info',
            format: winston.format.json(),
            transports: [
                new winston.transports.File({ filename: 'logs/threat-detection.log' })
            ]
        });
    }

    async assessRequest(req) {
        const assessment = {
            ip: req.ip,
            userAgent: req.get('User-Agent'),
            url: req.url,
            method: req.method,
            timestamp: new Date().toISOString(),
            riskFactors: [],
            riskScore: 0
        };

        // IP reputation analysis
        await this.analyzeIPReputation(assessment);

        // Request pattern analysis
        this.analyzeRequestPatterns(assessment, req);

        // User agent analysis
        this.analyzeUserAgent(assessment);

        // Geographic risk analysis
        await this.analyzeGeographicRisk(assessment);

        // Frequency analysis
        this.analyzeRequestFrequency(assessment);

        // Calculate overall risk
        assessment.riskScore = assessment.riskFactors.reduce((sum, factor) => sum + factor.score, 0);
        assessment.riskLevel = this.calculateRiskLevel(assessment.riskScore);

        // Log high-risk assessments
        if (assessment.riskLevel !== 'LOW') {
            this.logger.warn('Elevated threat assessment', assessment);
        }

        return assessment;
    }

    async analyzeIPReputation(assessment) {
        try {
            // Check cache first
            const cached = this.ipReputationCache.get(assessment.ip);
            if (cached && Date.now() - cached.timestamp < 3600000) { // 1 hour cache
                if (cached.isMalicious) {
                    assessment.riskFactors.push({
                        type: 'malicious_ip',
                        description: 'IP flagged as malicious in reputation databases',
                        score: 50,
                        severity: 'HIGH'
                    });
                }
                return;
            }

            // Simulate reputation check (integrate with actual threat intelligence)
            const reputation = await this.checkIPReputation(assessment.ip);

            this.ipReputationCache.set(assessment.ip, {
                isMalicious: reputation.isMalicious,
                categories: reputation.categories,
                timestamp: Date.now()
            });

            if (reputation.isMalicious) {
                assessment.riskFactors.push({
                    type: 'malicious_ip',
                    description: `IP reputation: ${reputation.categories.join(', ')}`,
                    score: reputation.severity === 'HIGH' ? 50 : 25,
                    severity: reputation.severity
                });
            }

        } catch (error) {
            this.logger.error('IP reputation analysis failed', {
                ip: assessment.ip,
                error: error.message
            });
        }
    }
}

module.exports = { EnterpriseSecurityConfiguration, AdvancedThreatDetectionService };
```

### Python/FastAPI Security Architecture

**Recommended Pattern:** Comprehensive async security with advanced threat detection and data protection

```python
# Comprehensive Security Configuration
from fastapi import FastAPI, Depends, HTTPException, status, Request, Response
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
from fastapi.middleware.cors import CORSMiddleware
from fastapi.middleware.trustedhost import TrustedHostMiddleware
from slowapi import Limiter, _rate_limit_exceeded_handler
from slowapi.util import get_remote_address
from slowapi.errors import RateLimitExceeded
import asyncio
import logging
import hashlib
import secrets
import json
from datetime import datetime, timedelta
from typing import Optional, Dict, List, Any
from pydantic import BaseModel
from cryptography.fernet import Fernet
import jwt

# Security logging configuration
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    handlers=[
        logging.FileHandler('logs/security.log'),
        logging.FileHandler('logs/security-audit.log'),
        logging.StreamHandler()
    ]
)

security_logger = logging.getLogger('enterprise_security')
audit_logger = logging.getLogger('security_audit')

class EnterpriseSecurityConfiguration:
    def __init__(self, app: FastAPI):
        self.app = app
        self.setup_rate_limiting()
        self.setup_middleware()
        self.setup_security_headers()
        self.threat_detector = AdvancedThreatDetectionService()
        self.data_protector = EnterpriseDataProtectionService()

    def setup_rate_limiting(self):
        # Advanced rate limiting with multiple tiers
        self.limiter = Limiter(key_func=get_remote_address)
        self.app.state.limiter = self.limiter
        self.app.add_exception_handler(RateLimitExceeded, _rate_limit_exceeded_handler)

    def setup_middleware(self):
        # CORS with strict origin validation
        allowed_origins = [
            "https://yourdomain.com",
            "https://app.yourdomain.com",
            "https://admin.yourdomain.com"
        ]

        self.app.add_middleware(
            CORSMiddleware,
            allow_origins=allowed_origins,
            allow_credentials=True,
            allow_methods=["GET", "POST", "PUT", "DELETE", "PATCH"],
            allow_headers=["Authorization", "Content-Type", "X-CSRF-Token"],
            expose_headers=["X-Request-ID", "X-Rate-Limit"]
        )

        # Trusted host validation
        self.app.add_middleware(
            TrustedHostMiddleware,
            allowed_hosts=["yourdomain.com", "*.yourdomain.com", "localhost"]
        )

        # Advanced security middleware
        @self.app.middleware("http")
        async def enterprise_security_middleware(request: Request, call_next):
            start_time = datetime.utcnow()
            request_id = secrets.token_hex(16)
            request.state.request_id = request_id

            # Security logging
            client_ip = get_remote_address(request)
            user_agent = request.headers.get("user-agent", "")

            security_logger.info(
                f"[{request_id}] {request.method} {request.url} from {client_ip}",
                extra={
                    "request_id": request_id,
                    "method": request.method,
                    "url": str(request.url),
                    "client_ip": client_ip,
                    "user_agent": user_agent
                }
            )

            # Comprehensive threat assessment
            threat_assessment = await self.threat_detector.assess_request_threat(request)
            request.state.threat_assessment = threat_assessment

            # Handle critical threats
            if threat_assessment.risk_level == ThreatLevel.CRITICAL:
                audit_logger.critical(
                    f"[{request_id}] Critical threat blocked",
                    extra={
                        "request_id": request_id,
                        "client_ip": client_ip,
                        "threat_assessment": threat_assessment.dict()
                    }
                )
                raise HTTPException(
                    status_code=status.HTTP_403_FORBIDDEN,
                    detail="Access denied due to security policy violation"
                )

            # Enhanced monitoring for high-risk requests
            if threat_assessment.risk_level == ThreatLevel.HIGH:
                request.state.requires_enhanced_monitoring = True

            try:
                response = await call_next(request)

                # Response security headers
                self.add_security_headers(response)

                # Performance and security logging
                process_time = (datetime.utcnow() - start_time).total_seconds()
                security_logger.info(
                    f"[{request_id}] Response {response.status_code} in {process_time:.4f}s",
                    extra={
                        "request_id": request_id,
                        "status_code": response.status_code,
                        "process_time": process_time,
                        "risk_level": threat_assessment.risk_level.value
                    }
                )

                return response

            except Exception as e:
                # Security exception logging
                security_logger.error(
                    f"[{request_id}] Request processing error: {str(e)}",
                    extra={
                        "request_id": request_id,
                        "error": str(e),
                        "client_ip": client_ip
                    },
                    exc_info=True
                )
                raise

    def add_security_headers(self, response: Response):
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
            "Cross-Origin-Resource-Policy": "same-origin"
        }

        for header, value in security_headers.items():
            response.headers[header] = value

class AdvancedThreatDetectionService:
    def __init__(self):
        self.ip_reputation_cache: Dict[str, Dict] = {}
        self.behavior_baselines: Dict[str, Dict] = {}
        self.suspicious_patterns = self._load_suspicious_patterns()
        self.threat_intelligence = ThreatIntelligenceService()

    async def assess_request_threat(self, request: Request) -> 'ThreatAssessment':
        """Comprehensive threat assessment for incoming requests"""
        assessment = ThreatAssessment(
            ip_address=get_remote_address(request),
            user_agent=request.headers.get("user-agent", ""),
            request_path=str(request.url.path),
            http_method=request.method,
            timestamp=datetime.utcnow()
        )

        # Multi-dimensional risk analysis
        await self._analyze_ip_reputation(assessment)
        await self._analyze_request_patterns(assessment, request)
        await self._analyze_user_agent(assessment)
        await self._analyze_geographic_risk(assessment)
        await self._analyze_request_frequency(assessment)
        await self._analyze_payload_threats(assessment, request)

        # Calculate overall risk score
        assessment.calculate_risk_score()

        # Log significant threats
        if assessment.risk_level != ThreatLevel.LOW:
            security_logger.warning(
                f"Elevated threat detected: {assessment.risk_level.value}",
                extra={
                    "threat_assessment": assessment.dict(),
                    "risk_factors": [rf.dict() for rf in assessment.risk_factors]
                }
            )

        return assessment

    async def _analyze_ip_reputation(self, assessment: 'ThreatAssessment'):
        """Analyze IP reputation using threat intelligence"""
        try:
            ip = assessment.ip_address

            # Check cache first
            cached = self.ip_reputation_cache.get(ip)
            if cached and (datetime.utcnow() - cached['timestamp']).total_seconds() < 3600:
                reputation_data = cached['data']
            else:
                reputation_data = await self.threat_intelligence.check_ip_reputation(ip)
                self.ip_reputation_cache[ip] = {
                    'data': reputation_data,
                    'timestamp': datetime.utcnow()
                }

            if reputation_data.is_malicious:
                assessment.add_risk_factor(
                    RiskFactor(
                        type="malicious_ip",
                        description=f"IP flagged as malicious: {', '.join(reputation_data.categories)}",
                        severity=RiskSeverity.HIGH,
                        score=50
                    )
                )

            if reputation_data.is_tor_exit_node:
                assessment.add_risk_factor(
                    RiskFactor(
                        type="tor_network",
                        description="Request from Tor exit node",
                        severity=RiskSeverity.MEDIUM,
                        score=30
                    )
                )

        except Exception as e:
            security_logger.error(f"IP reputation analysis failed: {e}")

    async def _analyze_payload_threats(self, assessment: 'ThreatAssessment', request: Request):
        """Analyze request payload for threats"""
        try:
            # Analyze query parameters
            query_string = str(request.query_params)
            for pattern_name, pattern in self.suspicious_patterns.items():
                if pattern.search(query_string):
                    assessment.add_risk_factor(
                        RiskFactor(
                            type="suspicious_payload",
                            description=f"Suspicious pattern detected in query: {pattern_name}",
                            severity=RiskSeverity.MEDIUM,
                            score=25
                        )
                    )

            # Analyze request body if present
            if request.method in ["POST", "PUT", "PATCH"]:
                try:
                    body = await request.body()
                    if body:
                        body_str = body.decode('utf-8', errors='ignore')
                        for pattern_name, pattern in self.suspicious_patterns.items():
                            if pattern.search(body_str):
                                assessment.add_risk_factor(
                                    RiskFactor(
                                        type="suspicious_payload",
                                        description=f"Suspicious pattern in body: {pattern_name}",
                                        severity=RiskSeverity.MEDIUM,
                                        score=25
                                    )
                                )
                except Exception:
                    pass  # Continue if body parsing fails

        except Exception as e:
            security_logger.error(f"Payload threat analysis failed: {e}")

class EnterpriseDataProtectionService:
    def __init__(self, master_key: str):
        self.master_key = master_key.encode()
        self.data_classifier = DataClassificationService()
        self.key_derivation = KeyDerivationService()
        self.audit_logger = logging.getLogger('data_protection_audit')

    async def encrypt_sensitive_data(self, data: str, data_type: DataType,
                                   context: Dict[str, Any]) -> EncryptedData:
        """Encrypt sensitive data with comprehensive protection"""
        try:
            # Classify data sensitivity
            classification = await self.data_classifier.classify_data(data, data_type)

            # Derive context-specific encryption key
            encryption_key = await self.key_derivation.derive_key(
                self.master_key,
                classification.level,
                context
            )

            # Select encryption algorithm based on classification
            algorithm = self._select_encryption_algorithm(classification)

            # Perform encryption
            fernet = Fernet(encryption_key)
            encrypted_bytes = fernet.encrypt(data.encode())

            # Create encrypted data object
            encrypted_data = EncryptedData(
                ciphertext=encrypted_bytes.decode(),
                algorithm=algorithm.name,
                key_derivation_info={
                    'classification': classification.level.value,
                    'context_hash': hashlib.sha256(
                        json.dumps(context, sort_keys=True).encode()
                    ).hexdigest()
                },
                timestamp=datetime.utcnow(),
                data_classification=classification
            )

            # Audit encryption operation
            self.audit_logger.info(
                "Data encryption completed",
                extra={
                    "data_type": data_type.value,
                    "classification": classification.level.value,
                    "context": context,
                    "timestamp": encrypted_data.timestamp.isoformat()
                }
            )

            return encrypted_data

        except Exception as e:
            self.audit_logger.error(
                "Data encryption failed",
                extra={
                    "data_type": data_type.value,
                    "context": context,
                    "error": str(e)
                },
                exc_info=True
            )
            raise DataProtectionException("Encryption operation failed") from e
```

## 📊 Success Criteria

### Security Architecture Effectiveness
- **Threat Coverage**: 100% of identified threats have appropriate mitigation controls
- **Control Effectiveness**: >95% of security controls functioning as designed
- **Incident Response**: <30 minutes mean time to detect and respond to security incidents
- **Compliance Posture**: 100% compliance with applicable regulatory requirements

### Implementation Quality Metrics
- **Technology Alignment**: Security controls match framework capabilities and best practices
- **Defense Depth**: Multiple security layers implemented across all system components
- **Risk Mitigation**: >90% reduction in identified risk exposure through implemented controls
- **Monitoring Coverage**: 100% of critical assets under continuous security monitoring

## 🎯 Deliverables

Upon completion of comprehensive security architecture and threat modeling:

- ✅ **Security Architecture Document** with comprehensive controls and frameworks mapping
- ✅ **Threat Model Report** with STRIDE analysis and detailed risk assessment
- ✅ **Security Control Matrix** with implementation specifications and testing procedures
- ✅ **Zero Trust Architecture Plan** with implementation roadmap and migration strategy
- ✅ **Incident Response Framework** with automated detection and response capabilities
- ✅ **Compliance Mapping** with regulatory requirements and technical control alignment
- ✅ **Security Monitoring Setup** with SIEM integration and comprehensive logging
- ✅ **Data Protection Framework** with encryption, classification, and access controls

## 🔄 Chatmode Transition

To complete the comprehensive security implementation:

**Switch to security-controls-implementation chatmode** to establish detailed security control implementations, monitoring systems, and operational security procedures that complement your security architecture and threat modeling foundation.

---

*This comprehensive security architecture and threat modeling provides the foundation for robust enterprise security through systematic threat analysis, defense-in-depth controls, and technology-adaptive implementations that protect business assets while enabling secure operations.*