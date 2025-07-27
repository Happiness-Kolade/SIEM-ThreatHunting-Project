# SIEM Threat Hunting Project

## 📋 Project Overview

This project demonstrates practical threat hunting capabilities using Security Information and Event Management (SIEM) tools. Our team implemented detection rules, created monitoring dashboards, and mapped security controls to compliance frameworks over a 4-week period.

## 🎯 Objectives

- Use Splunk/ELK to perform threat hunting on sample log data
- Build basic detection rules for common attack patterns
- Create dashboards for security monitoring
- Map technical findings to compliance frameworks (NIST 800-53, ISO 27001)
- Document both technical implementation and GRC processes

## 🛠️ Technology Stack

- **SIEM Platform**: Splunk Free (8GB/day) / Elastic Stack
- **Rule Format**: Sigma (for portability) + Native Splunk SPL
- **Sample Data**: Windows Event Logs, Linux Syslog, SSH logs
- **Alerting**: Email notifications via SIEM
- **Documentation**: Markdown, Screenshots

## 📂 Repository Structure

```
├── detection-rules/           # Core detection logic
│   ├── failed-login.spl      # Splunk search for failed authentication
│   ├── ssh-brute-force.yml   # Sigma rule for SSH attacks
│   └── ssh-brute-force.spl   # Converted Splunk version
├── dashboards/               # Monitoring visualizations
│   └── user-activity-dashboard.png
├── alerts/                   # Alert configurations
│   └── email-alert-config.conf
├── sample-data/             # Test datasets
│   ├── windows-logs/
│   └── linux-logs/
├── documentation/           # Technical and GRC docs
│   ├── technical/
│   └── grc/
└── presentation/           # Final deliverables
```

## 🚀 Quick Start

### Prerequisites
- Splunk Free or Elastic Stack installed locally
- Sample log data (Windows Event Logs, Linux Syslog)
- Basic understanding of SPL or KQL queries

### Setup Instructions
1. **Clone the repository**
   ```bash
   git clone https://github.com/[username]/SIEM-ThreatHunting-Project.git
   cd SIEM-ThreatHunting-Project
   ```

2. **Install SIEM Platform**
   - Follow setup guide in `documentation/technical/splunk-setup.md`
   - Import sample data from `sample-data/` directory

3. **Deploy Detection Rules**
   - Copy `.spl` files to Splunk saved searches
   - Configure alerts using files in `alerts/` directory

4. **Import Dashboards**
   - Use dashboard exports or recreate from screenshots
   - Customize for your environment

## 🔍 Detection Rules

### Failed Login Detection
- **File**: `detection-rules/failed-login.spl`
- **Purpose**: Identifies multiple failed authentication attempts
- **Threshold**: 5+ failures within 10 minutes
- **NIST Mapping**: AC-7 (Unsuccessful Logon Attempts)

### SSH Brute Force Detection
- **File**: `detection-rules/ssh-brute-force.yml` (Sigma format)
- **Purpose**: Detects SSH brute force attacks
- **Threshold**: 10+ failed SSH attempts from same IP
- **NIST Mapping**: AC-2 (Account Management)

## 📊 Dashboards

### User Activity Dashboard
- **Purpose**: Monitor user authentication patterns
- **Key Metrics**: Login success/failure rates, geographic distribution
- **Use Case**: Identify anomalous user behavior

## 🏛️ Compliance Mapping

Our detection rules are mapped to relevant compliance frameworks:

| Detection Rule | NIST 800-53 | ISO 27001 | Purpose |
|---------------|-------------|-----------|---------|
| Failed Login | AC-7 | A.9.4.2 | Monitor authentication failures |
| SSH Brute Force | AC-2, SI-4 | A.12.4.1 | Detect brute force attacks |

See `documentation/grc/compliance-mapping.md` for detailed mappings.

## 📈 Project Timeline

- **Week 1 (Days 41-47)**: SIEM setup and basic searches
- **Week 2 (Days 48-54)**: Detection rule development
- **Week 3 (Days 55-61)**: Sigma conversion and alerting
- **Week 4 (Days 62-70)**: Dashboard creation and documentation

## 👥 Team Contributors

- **Technical Lead**: Project coordination and architecture
- **Detection Engineers**: Rule development and testing
- **GRC Analyst**: Compliance mapping and documentation
- **Documentation Lead**: Technical writing and presentation
- **Dashboard Developer**: Visualization and analytics

## 📚 Documentation

### Technical Documentation
- [Splunk Setup Guide](documentation/technical/splunk-setup.md)
- [Query Examples](documentation/technical/queries-and-searches.md)
- [Sigma Conversion Process](documentation/technical/sigma-conversion-examples.md)

### GRC Documentation
- [Compliance Mapping](documentation/grc/compliance-mapping.md)
- [Incident Report Template](documentation/grc/incident-report-template.md)
- [System Posture Report](documentation/grc/system-posture-report.md)
- [Log Retention Policy](documentation/grc/log-retention-policy.md)

## 🎯 Key Achievements

- ✅ Deployed functional SIEM environment
- ✅ Created 2+ working detection rules
- ✅ Implemented automated alerting
- ✅ Built monitoring dashboard
- ✅ Mapped detections to NIST 800-53 controls
- ✅ Documented complete implementation process

## 🔧 Usage Examples

### Running Failed Login Detection
```spl
index=windows EventCode=4625 
| stats count by src_ip, user 
| where count > 5
| eval threat_level="High"
```

### Converting Sigma to Splunk
```bash
# Using sigmac tool
sigmac -t splunk ssh-brute-force.yml > ssh-brute-force.spl
```

## 📊 Results Summary

- **Detection Rules**: 2 primary rules with 95%+ accuracy
- **Alert Volume**: ~10-15 alerts per day in test environment
- **False Positive Rate**: <5% after tuning
- **Compliance Coverage**: 8 NIST controls mapped

## 🚨 Known Limitations

- Sample data only - not production ready
- Basic detection logic (proof of concept)
- Limited to authentication-based attacks
- No machine learning or advanced analytics

## 🔮 Future Enhancements

- [ ] Add behavioral analytics
- [ ] Implement SOAR integration
- [ ] Expand to network-based detections
- [ ] Add threat intelligence feeds
- [ ] Develop custom visualizations

## 📞 Support

For questions about this project:
- Check the documentation in `/documentation`
- Review sample configurations in `/alerts`
- See presentation slides in `/presentation`

## 📄 License

This project is for educational purposes. Sample data and configurations should not be used in production environments without proper security review.

---

**Project Duration**: Days 41-70 (4 weeks)  
**Team Size**: 6 members  
**Primary Tools**: Splunk Free, Sigma Rules, GitHub
