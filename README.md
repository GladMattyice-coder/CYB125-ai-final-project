# Windows Baseline Configuration Snapshot Collector
## CYB 125 Final Project — Part 1: Project Plan

**Student name:** Mati(son) Lund
**Date:** May 8th, 2026

---

## About this Project
The purpose of this script is to collect important information from a Windows virtual machine and save it into a JSON file as a system snapshot. The script gathers data about the computer’s configuration, including things like running processes,
installed software, network settings, and user account information. This project could be useful for security analysts or system administrators who need to monitor systems and look for changes over time.
The snapshot can later be compared with another snapshot from the same machine to help detect unauthorized changes or suspicious activity.
 
---

## Approach

This project will collect information from three main sources within the Windows operating system. The first source is the Windows Registry using the winreg Python module,
which allows the script to access configuration settings and installed software information. The second source is performance counters collected through the typeperf command 
to gather information about system performance and resource usage. The final source is different Windows command-line utilities, which can provide details about processes, users, 
networking, scheduled tasks, and other system information. All of this data will be gathered and organized into a structured JSON format.
---

## Data Dictionary
{
    "snapshot_metadata": {
        "schema_version": 
        "timestamp_utc": 
        "hostname": 
        "generated_by_user": 
        "elevated": 
        "script_version": 
        "python_version": 
        "collection_duration_seconds": 
        "collection_warnings": []
    },
    "system_identity": {
        "computer_name": 
        "os_name": 
        "os_build": 
        "os_edition": 
        "registered_owner": 
        "registered_organization": 
        "product_id": 
        "os_version": 
        "install_date_utc": 
        "last_boot_utc": 
        "uptime_seconds": 
        "time_zone": 
        "domain_or_workgroup": 
        "is_domain_joined": 
    },
    "hardware_profile": {
        "cpu": {
            "name": 
            "manufacturer": 
            "max_clock_mhz": 
            "architecture": 
            "logical_processors": 
            "physical_cores": 
        },
        "memory": {
            "total_physical_bytes": 
        },
        "bios": {
            "manufacturer": 
            "version": 
            "release_date": 
        },
        "system": {
            "manufacturer": 
            "model": 
        },
        "logical_disks": [
            {
                "drive_letter": 
                "filesystem": 
                "total_size_bytes": 
                "free_space_bytes": 
            }
        ]
    },
    "network_configuration": {
        "primary_dns_suffix": 
        "adapters": [
            {
                "name": 
                "description": 
                "mac_address": 
                "dhcp_enabled": 
                "ipv4_addresses": [],
                "ipv4_subnet_mask": 
                "default_gateway": 
                "dns_servers": []
            }
        ]
    },
    "listening_ports": [
        {
            "protocol": 
            "local_address": 
            "local_port": 
            "state": 
            "owning_pid": 
            "owning_process_name": 
        }
    ],
    "local_user_accounts": {
        "current_user": 
        "users": [
            {
                "username": 
                "full_name": 
                "sid": 
                "disabled": 
                "password_required": 
                "password_changeable": 
                "password_expires": 
                "last_logon_utc": 
            }
        ],
        "administrators_group_members": []
    },
    "password_policy": {
        "minimum_password_length": 
        "minimum_password_age_days": 
        "maximum_password_age_days": 
        "password_history_length": 
        "lockout_threshold": 
        "lockout_duration_minutes": 
        "lockout_observation_window_minutes": 
        "force_logoff_after_minutes": 
    },
    "auto_start_services": [
        {
            "name": 
            "display_name": 
            "state": 
            "start_type": 
            "executable_path": 
            "log_on_as": 
        }
    ],
    "running_processes": [
        {
            "pid": 
            "parent_pid": 
            "name": 
            "executable_path": 
            "command_line": 
        }
    ],
    "installed_software": [
        {
            "display_name": 
            "display_version": 
            "publisher": 
            "install_date": 
            "registry_hive": 
            "is_64_bit": 
        }
    ],
    "installed_hotfixes": [
        {
            "hotfix_id": 
            "description": 
            "installed_on": 
            "installed_by": 
        }
    ],
    "persistence_locations": {
        "hklm_run": [
            {
                "name": 
                "value": 
            },
        ],
        "hkcu_run": [
            {
                "name": 
                "value": 
            }
        ],
        "hklm_run_once": [],
        "hkcu_run_once": [
            {
                "name": 
                "value": 
            }
        ],
        "all_users_startup_folder": {
            "path": 
            "files": []
        },
        "current_user_startup_folder": {
            "path": 
            "files": []
        }
    },
    "scheduled_tasks": [
        {
            "task_name": 
            "status": 
            "next_run_time": 
            "last_run_time": 
            "last_result": 
            "author": 
            "task_to_run": 
        }
    ],
    "security_posture": {
        "firewall": {
            "domain_profile": {
                "state": 
                "default_inbound_action": 
                "default_outbound_action": 
                "logging_dropped_connections": 
            },
            "private_profile": {
                "state": 
                "default_inbound_action": 
                "default_outbound_action": 
                "logging_dropped_connections": 
            },
            "public_profile": {
                "state": 
                "default_inbound_action": 
                "default_outbound_action": 
                "logging_dropped_connections": 
            }
        },
        "windows_defender": {
            "antivirus_enabled": 
            "real_time_protection_enabled": 
            "antivirus_signature_age_days": 
            "antivirus_signature_version": 
        },
        "uac": {
            "enabled": 
            "consent_prompt_behavior_admin": 
            "prompt_on_secure_desktop": 
        },
        "bitlocker": {
            "system_drive_protection_status": 
            "encryption_method": 
            "encryption_percentage": 
        }
    },
    "performance_snapshot": {
        "sample_timestamp_utc": 
        "cpu_total_percent": 
        "memory": {
            "available_bytes": 
        },
        "disk_system_volume": {
            "reads_per_sec": 
            "writes_per_sec": 
        },
        "process_count": 
    },
    "network_shares": [
        {
            "share_name": 
            "local_path": 
            "description": 
            "is_administrative": 
        }
    ]
}
```
---

## Configuration Areas

##ALL OF THESE NEED TO A MATCH A SET STANDARD 

## 1. snapshot_metadata
Its a snapshot of data at a particular moment in time.

## 2. system_identity
System identity is a way of operating systems.

## 3. hardware_profile
Comparing compatability issues, speed MHZ.

## 4. network_configuration
 It would be important to have DHCP enabled, in case we wanted to compare to static.

## 5. listening_ports
If you have a baseline local port and state, but then you notice an unwanted process starts running.

## 6. local_user_accounts
Adminsters the rule of least privlege. 

## 7. password_policy
Important to keep tabs on password credentials (security reasons obviously).

## 8. auto_start_services
Important to know what is supposed to autostart as the base line.

## 9. running_processes
Paths are curreated on purpose by admins for baseline, if something is running from a strange location, "???"

## 10. installed_software
Necessary to control software for the appropriate enviornments

## 11. installed_hotfixes
Important to know what it is you're installing, it might break the system and you need to know what it was 

## 12. persistence_locations
Advantage of controlling what runs, how many times, and if its automatic.

## 13. scheduled_tasks
This baseline is good for monitoring the mundane security

## 14. security_posture
Bridges the gap between the human detection of malware/security threats

## 15. performance_snapshot
Its important to know if the baseline/standard you're currently working at is keeping up with the necessary performance

## 16. network_shares
Important for the baseline that certain responsibilities are given to trusted admins to share specific information

---

## Strategy

I plan to use AI in the following way....

Three prompts I plan to use:

1. I ask AI to read directions for me if I am confused by the original
2. If I am unsure and stuck and no other recourses available, I ask for hints and am very specific to say "Dont give me the answer."
3. I realized that AI will give me written responses if I ask a question, so I learned to specify that I would like cliff notes and guidelines rather than a cheat.

---

## Milestones

The project is structured around eight milestones, each one designed to produce a working JSON file with an additional section implemented. The milestone structure isn't just a grading convenience, it's a deliberate AI-collaboration pattern. 

When students use AI well, they treat it like a pair programmer: they bring it small, well-scoped problems, ask it to explain things rather than just produce things, and verify its answers against an authoritative source (the textbook, the official Python docs, or their own running code). The output is code they understand and could rewrite from scratch.

The eight-milestone structure exists to force responsible AI usage. Each milestone is small enough that you can hold the whole thing in your head. Each milestone has a specific Python concept attached to it, so you know what you're supposed to be learning. Each milestone has a suggested AI prompt that asks for explanation, not code.

Your goal is not to finish the project as fast as possible. Your goal is to finish the project understanding what you built. Those are different goals. The milestone structure pushes you toward the second one.



---

## Notes for the Instructor
Anything you want to put here...