---
description: Create comprehensive deployment and packaging solutions for desktop applications with advanced cross-platform distribution, automated update mechanisms, code signing, and professional installation packages. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
  - vscodeAPI
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `deployment-engineer` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Desktop Application Deployment and Packaging

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Desktop Packaging Solutions
- **Cross-Platform Package Generation**: Create native installation packages for Windows, macOS, and Linux with platform-specific optimizations
- **Professional Installation Experience**: Design user-friendly installation wizards with customization options and proper system integration
- **Application Bundling**: Bundle all dependencies, resources, and runtime requirements into standalone deployment packages
- **Package Signing and Verification**: Implement code signing and digital certificates for security and trust verification

### Automated Distribution and Deployment
- **Continuous Deployment Pipeline**: Automate package generation and distribution through CI/CD pipelines with quality gates
- **Multi-Channel Distribution**: Support multiple distribution channels including app stores, direct download, and enterprise deployment
- **Release Management**: Implement versioning, release notes, and rollback capabilities for desktop application releases
- **Enterprise Deployment**: Create enterprise-specific deployment solutions with mass deployment and configuration management

### Auto-Update and Maintenance Systems
- **Automatic Update Mechanisms**: Implement secure auto-update systems with delta updates and background installation
- **Update Scheduling and Control**: Provide user control over update timing with enterprise policy management
- **Rollback and Recovery**: Design rollback mechanisms for failed updates with data protection and system recovery
- **Update Analytics**: Track update success rates, user adoption, and system compatibility metrics

### Security and Compliance Integration
- **Code Signing and Trust**: Implement comprehensive code signing with certificate management and trust validation
- **Sandboxing and Permissions**: Configure application sandboxing and permission models for enhanced security
- **Compliance Packaging**: Ensure packaging meets industry-specific compliance requirements and security standards
- **Vulnerability Management**: Integrate security scanning and vulnerability assessment into packaging workflows

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Technology Stack Analysis and Platform Requirements
```
1. Read copilot.instructions.md to extract:
   - Desktop framework and programming language requirements
   - Target platform specifications and architecture support
   - Business domain security and compliance requirements
   - Distribution method preferences and constraints

2. Platform Requirement Analysis:
   - Analyze target operating systems and minimum version requirements
   - Evaluate hardware architecture support (x64, ARM, universal binaries)
   - Assess platform-specific features and integration requirements
   - Review app store and distribution channel requirements
```

### 2. Package Configuration and Build Setup
```
1. Packaging Tool Selection and Configuration:
   - Configure appropriate packaging tools for each target platform
   - Set up build environments and dependency management
   - Configure code signing certificates and security credentials
   - Implement cross-platform build automation

2. Package Structure Design:
   - Design application bundle structure and resource organization
   - Configure runtime dependencies and library inclusion
   - Set up application metadata and manifest files
   - Plan icon resources and visual branding integration
```

### 3. Installation and Distribution Implementation
```
1. Installation Package Creation:
   - Generate platform-specific installers with customization options
   - Implement uninstall procedures and system cleanup
   - Configure system integration including file associations and shortcuts
   - Set up application registration and Windows registry entries

2. Distribution Channel Setup:
   - Configure app store submission packages and metadata
   - Set up direct download infrastructure with secure hosting
   - Implement enterprise deployment packages with group policy integration
   - Create portable deployment options for specialized use cases
```

### 4. Auto-Update System Implementation
```
1. Update Infrastructure Setup:
   - Implement secure update server infrastructure with CDN integration
   - Configure update manifest generation and versioning
   - Set up delta update generation for bandwidth optimization
   - Implement update verification and integrity checking

2. Client-Side Update Implementation:
   - Integrate auto-update client with background checking and notification
   - Implement staged updates with rollback capabilities
   - Configure user preference management and enterprise policies
   - Set up update analytics and error reporting
```

### 5. Security, Testing, and Maintenance
```
1. Security and Compliance Implementation:
   - Implement comprehensive code signing with certificate management
   - Configure application sandboxing and permission controls
   - Set up security scanning and vulnerability assessment
   - Implement compliance validation and audit trails

2. Testing and Quality Assurance:
   - Create automated testing for package generation and installation
   - Implement cross-platform compatibility testing
   - Set up update mechanism testing and rollback validation
   - Create performance testing for installation and update processes
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Packaging Quality and Compatibility
- **Cross-Platform Support**: Native packages generated for all target platforms with proper system integration
- **Installation Experience**: Professional installation experience with proper user guidance and system integration
- **Dependency Management**: All dependencies properly bundled with version compatibility and conflict resolution
- **Package Integrity**: Signed packages with proper certificate validation and trust verification

### ✅ Distribution and Deployment Excellence
- **Automated Generation**: Automated package generation through CI/CD pipelines with quality validation
- **Multi-Channel Support**: Support for app stores, direct download, and enterprise deployment channels
- **Version Management**: Proper versioning with release notes and backward compatibility management
- **Enterprise Deployment**: Enterprise-ready deployment with mass installation and configuration management

### ✅ Auto-Update System Reliability
- **Update Mechanism**: Reliable auto-update system with secure download and verification
- **User Control**: Appropriate user control over updates with enterprise policy management
- **Rollback Capability**: Robust rollback mechanisms for failed updates with data protection
- **Performance Optimization**: Efficient delta updates with bandwidth optimization and background processing

### ✅ Security and Compliance
- **Code Signing**: Comprehensive code signing with proper certificate management and validation
- **Security Integration**: Application sandboxing and permission controls meeting security requirements
- **Compliance Validation**: Packaging meets industry-specific compliance and regulatory requirements
- **Vulnerability Management**: Security scanning integrated into packaging workflow with remediation

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with other chatmodes for complete desktop application development
- **CI/CD Integration**: Advanced GitHub Actions workflows for automated packaging and distribution
- **Configuration Adaptation**: Proper adaptation to desktop technology stack and business domain requirements
- **Quality Automation**: Automated testing and validation for packaging and deployment processes

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Electron Application Cross-Platform Packaging
```yaml
Context: Cross-platform Electron application requiring distribution through multiple channels
Technology Stack: Detected from copilot.instructions.md (Electron, React, TypeScript, Windows/macOS/Linux)
Business Domain: Productivity application with enterprise and consumer distribution

Desktop Packaging Focus:
- Cross-platform Electron packaging with native installers for Windows, macOS, and Linux
- Auto-update system with secure download and delta updates
- App store submission packages for Microsoft Store and Mac App Store
- Enterprise deployment with MSI packages and group policy integration

GitHub Copilot Workflow:
1. deployment-engineer chatmode → Configure Electron Builder and cross-platform packaging automation
2. security-engineer chatmode → Implement code signing and certificate management
3. qa-engineer chatmode → Create automated testing for installation and update processes
4. frontend-engineer chatmode → Optimize application bundling and resource management

Expected Deliverables:
- Electron Builder configuration with cross-platform package generation
- GitHub Actions workflow for automated packaging and distribution
- Auto-update system with Electron's built-in updater and secure hosting
- Code signing setup for Windows and macOS with certificate management
```

### Scenario 2: WPF Enterprise Application Deployment
```yaml
Context: Enterprise WPF application requiring secure deployment and management
Technology Stack: Enterprise setup (.NET Framework, WPF, ClickOnce, Group Policy, WSUS)
Business Domain: Enterprise resource planning with strict security and compliance requirements

Desktop Packaging Focus:
- ClickOnce deployment with automatic updates and security validation
- MSI packaging for enterprise deployment with custom installation options
- Group Policy integration for enterprise configuration management
- WSUS integration for enterprise update management and control

GitHub Copilot Workflow:
1. deployment-engineer chatmode → Configure ClickOnce and MSI packaging with enterprise features
2. security-engineer chatmode → Implement enterprise security and certificate management
3. data-engineer chatmode → Configure database deployment and migration automation
4. qa-engineer chatmode → Create enterprise testing and validation procedures

Expected Deliverables:
- ClickOnce deployment with automatic updates and enterprise security
- MSI packages with custom installation options and group policy support
- Enterprise deployment documentation and administrative tools
- WSUS integration for centralized update management and reporting
```

### Scenario 3: Qt Application Multi-Platform Distribution
```yaml
Context: Qt C++ application requiring professional packaging for scientific and engineering users
Technology Stack: Scientific setup (C++, Qt, CMake, Windows/macOS/Linux, professional distribution)
Business Domain: Scientific software with professional licensing and distribution requirements

Desktop Packaging Focus:
- Qt deployment with platform-specific packaging and dependency management
- Professional licensing integration with activation and validation
- Scientific software distribution through specialized channels
- Cross-platform compatibility with hardware acceleration support

GitHub Copilot Workflow:
1. deployment-engineer chatmode → Configure Qt deployment and cross-platform packaging
2. security-engineer chatmode → Implement licensing validation and software protection
3. qa-engineer chatmode → Create compatibility testing across platforms and hardware configurations
4. frontend-engineer chatmode → Optimize Qt application performance and resource usage

Expected Deliverables:
- Qt deployment configuration with windeployqt, macdeployqt, and Linux packaging
- Professional licensing system with activation and validation
- Cross-platform installers with hardware detection and optimization
- Scientific software distribution packages for specialized channels
```

### Scenario 4: JavaFX Application Enterprise Packaging
```yaml
Context: JavaFX application requiring enterprise deployment with Java runtime bundling
Technology Stack: Java setup (Java, JavaFX, Maven, jpackage, Windows/macOS/Linux)
Business Domain: Business application with enterprise deployment and Java runtime management

Desktop Packaging Focus:
- jpackage deployment with bundled Java runtime and native installers
- Enterprise deployment with centralized configuration and update management
- Java runtime management with automatic updates and compatibility validation
- Cross-platform business application distribution with professional branding

GitHub Copilot Workflow:
1. deployment-engineer chatmode → Configure jpackage and Maven for enterprise deployment
2. qa-engineer chatmode → Create Java runtime compatibility testing and validation
3. security-engineer chatmode → Implement Java security policies and certificate management
4. frontend-engineer chatmode → Optimize JavaFX application startup and performance

Expected Deliverables:
- jpackage configuration with bundled Java runtime and native installers
- Maven build automation with cross-platform packaging and distribution
- Enterprise deployment packages with centralized configuration management
- Java runtime update system with compatibility validation and rollback
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Desktop Deployment and Packaging → deployment-engineer chatmode (lead)
├─ Desktop Security Implementation → security-engineer chatmode
├─ Desktop Application Optimization → frontend-engineer chatmode
├─ Database Integration → data-engineer chatmode
├─ Quality Assurance → qa-engineer chatmode
└─ API Integration → api-engineer chatmode
```

### Context Handoff Information
- **To security-engineer**: Code signing requirements, certificate management, security policies, compliance validation
- **To frontend-engineer**: Application optimization, resource bundling, performance requirements, user experience
- **To data-engineer**: Database deployment, migration scripts, data packaging, backup integration
- **To qa-engineer**: Testing automation, compatibility validation, installation testing, update verification
- **To api-engineer**: API endpoint configuration, service integration, update server setup, analytics integration

### GitHub Actions Integration
- **Automated Packaging**: Comprehensive GitHub Actions workflows for cross-platform package generation
- **Distribution Automation**: Automated distribution to multiple channels including app stores and enterprise systems
- **Quality Gates**: Automated testing for installation, updates, and compatibility across platforms
- **Security Validation**: Automated security scanning and certificate validation in packaging workflow

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Desktop Framework**: Automatically configures packaging for Electron, WPF, Qt, JavaFX, or other desktop frameworks
- **Target Platforms**: Optimizes packaging for Windows, macOS, Linux, or specific platform combinations
- **Business Domain**: Adapts distribution strategy to enterprise, consumer, scientific, or specialized market requirements
- **Security Requirements**: Implements appropriate code signing, licensing, and security measures based on compliance needs
- **Distribution Strategy**: Configures distribution channels based on app store, enterprise, or direct distribution preferences

**The deployment-engineer chatmode will automatically analyze project configuration and desktop requirements to deliver optimal deployment and packaging solutions while maintaining the functional requirements specified above.**
```

**Platform-specific analysis:**
```bash
# Check target platforms
uname -a
echo "Current platform: $(uname -s)"

# Windows deployment tools
where innosetup 2>/dev/null || echo "Inno Setup not found"
where "C:\Program Files (x86)\NSIS\makensis.exe" 2>/dev/null || echo "NSIS not found"

# macOS deployment tools
which pkgbuild 2>/dev/null || echo "pkgbuild not found"
which create-dmg 2>/dev/null || echo "create-dmg not found"

# Linux deployment tools
which dpkg-deb 2>/dev/null || echo "dpkg-deb not found"
which rpmbuild 2>/dev/null || echo "rpmbuild not found"
which appimage-builder 2>/dev/null || echo "appimage-builder not found"
```

### Step 2: Application Technology Analysis
```bash
# Python applications
find . -name "*.py" -o -name "requirements.txt" -o -name "setup.py" | head -5
ls -la dist/ build/ *.spec 2>/dev/null

# C++ applications
find . -name "*.cpp" -o -name "CMakeLists.txt" -o -name "Makefile" | head -5
ls -la bin/ Release/ Debug/ 2>/dev/null

# .NET applications
find . -name "*.csproj" -o -name "*.sln" | head -5
ls -la bin/Release/ bin/Debug/ publish/ 2>/dev/null

# Electron applications
find . -name "package.json" -o -name "electron-builder.yml" | head -5
ls -la dist/ out/ 2>/dev/null
```

## Technology-Specific Deployment Solutions

**⚠️ IMPORTANT: Select deployment approach based on copilot.instructions.md technology and platform specification**

### Python Desktop Application Deployment

**Use when copilot.instructions.md specifies: Python, wxPython, desktop**

```python
# build_scripts/build_config.py - Build configuration management
import os
import sys
import platform
import json
from pathlib import Path
from typing import Dict, List, Optional

class BuildConfig:
    def __init__(self, config_file: str = "build_config.json"):
        self.config_file = Path(config_file)
        self.config = self._load_config()
        self.platform = platform.system().lower()

    def _load_config(self) -> Dict:
        """Load build configuration from file"""
        default_config = {
            "app_name": "Desktop Application",
            "app_version": "1.0.0",
            "app_author": "Your Company",
            "app_description": "Desktop application built with Python",
            "app_icon": "assets/icon.ico",
            "main_script": "main.py",
            "hidden_imports": [
                "wx", "sqlite3", "logging", "json", "threading"
            ],
            "data_files": [
                ("assets", "assets/*"),
                ("config", "config/*"),
                ("data", "data/*.sql")
            ],
            "exclude_modules": [
                "tkinter", "test", "unittest", "pdb", "pydoc"
            ],
            "target_platforms": ["windows", "linux", "macos"],
            "signing": {
                "enabled": False,
                "certificate_path": "",
                "certificate_password": ""
            },
            "auto_update": {
                "enabled": True,
                "update_server": "https://your-server.com/updates",
                "check_interval": 3600
            }
        }

        if self.config_file.exists():
            with open(self.config_file, 'r') as f:
                config = json.load(f)
                # Merge with defaults
                for key, value in default_config.items():
                    if key not in config:
                        config[key] = value
                return config
        else:
            # Create default config
            with open(self.config_file, 'w') as f:
                json.dump(default_config, f, indent=2)
            return default_config

    def get_pyinstaller_spec(self) -> str:
        """Generate PyInstaller spec file content"""
        hidden_imports = ", ".join([f"'{imp}'" for imp in self.config["hidden_imports"]])
        datas = []

        for data_folder, pattern in self.config["data_files"]:
            datas.append(f"('{pattern}', '{data_folder}')")

        datas_str = ", ".join(datas)

        spec_content = f'''# -*- mode: python ; coding: utf-8 -*-
import os
from pathlib import Path

block_cipher = None

a = Analysis(
    ['{self.config["main_script"]}'],
    pathex=[],
    binaries=[],
    datas=[{datas_str}],
    hiddenimports=[{hidden_imports}],
    hookspath=[],
    hooksconfig={{}},
    runtime_hooks=[],
    excludes={self.config["exclude_modules"]},
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=block_cipher,
    noarchive=False,
)

pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)

exe = EXE(
    pyz,
    a.scripts,
    a.binaries,
    a.zipfiles,
    a.datas,
    [],
    name='{self.config["app_name"].replace(" ", "_")}',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    upx_exclude=[],
    runtime_tmpdir=None,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
    icon='{self.config["app_icon"]}',
    version='version_info.py'
)
'''
        return spec_content

    def get_version_info(self) -> str:
        """Generate Windows version info file"""
        if self.platform != "windows":
            return ""

        version_parts = self.config["app_version"].split(".")
        while len(version_parts) < 4:
            version_parts.append("0")

        version_tuple = ", ".join(version_parts)

        return f'''VSVersionInfo(
  ffi=FixedFileInfo(
    filevers=({version_tuple}),
    prodvers=({version_tuple}),
    mask=0x3f,
    flags=0x0,
    OS=0x40004,
    fileType=0x1,
    subtype=0x0,
    date=(0, 0)
  ),
  kids=[
    StringFileInfo(
      [
        StringTable(
          u'040904B0',
          [StringStruct(u'CompanyName', u'{self.config["app_author"]}'),
           StringStruct(u'FileDescription', u'{self.config["app_description"]}'),
           StringStruct(u'FileVersion', u'{self.config["app_version"]}'),
           StringStruct(u'InternalName', u'{self.config["app_name"]}'),
           StringStruct(u'LegalCopyright', u'© {self.config["app_author"]}'),
           StringStruct(u'OriginalFilename', u'{self.config["app_name"].replace(" ", "_")}.exe'),
           StringStruct(u'ProductName', u'{self.config["app_name"]}'),
           StringStruct(u'ProductVersion', u'{self.config["app_version"]}')])
      ]
    ),
    VarFileInfo([VarStruct(u'Translation', [1033, 1200])])
  ]
)'''
```

```python
# build_scripts/builder.py - Cross-platform build system
import subprocess
import shutil
import zipfile
from pathlib import Path
from build_config import BuildConfig
import logging

class DesktopAppBuilder:
    def __init__(self, config: BuildConfig):
        self.config = config
        self.logger = logging.getLogger(__name__)
        self.dist_dir = Path("dist")
        self.build_dir = Path("build")

    def clean_build(self):
        """Clean previous build artifacts"""
        if self.dist_dir.exists():
            shutil.rmtree(self.dist_dir)
        if self.build_dir.exists():
            shutil.rmtree(self.build_dir)

        # Remove PyInstaller files
        for pattern in ["*.spec", "version_info.py"]:
            for file in Path(".").glob(pattern):
                file.unlink(missing_ok=True)

    def build_executable(self) -> bool:
        """Build executable using PyInstaller"""
        try:
            # Create spec file
            spec_content = self.config.get_pyinstaller_spec()
            with open("app.spec", "w") as f:
                f.write(spec_content)

            # Create version info for Windows
            if self.config.platform == "windows":
                version_content = self.config.get_version_info()
                with open("version_info.py", "w") as f:
                    f.write(version_content)

            # Run PyInstaller
            cmd = [
                "pyinstaller",
                "--clean",
                "--noconfirm",
                "app.spec"
            ]

            result = subprocess.run(cmd, capture_output=True, text=True)
            if result.returncode != 0:
                self.logger.error(f"PyInstaller failed: {result.stderr}")
                return False

            self.logger.info("Executable built successfully")
            return True

        except Exception as e:
            self.logger.error(f"Build failed: {e}")
            return False

    def create_windows_installer(self) -> bool:
        """Create Windows installer using Inno Setup"""
        if self.config.platform != "windows":
            return True

        iss_content = self._get_inno_setup_script()
        iss_file = Path("installer.iss")

        with open(iss_file, "w") as f:
            f.write(iss_content)

        try:
            # Try to find Inno Setup
            inno_paths = [
                "C:\\Program Files (x86)\\Inno Setup 6\\ISCC.exe",
                "C:\\Program Files\\Inno Setup 6\\ISCC.exe",
                "iscc.exe"  # If in PATH
            ]

            inno_exe = None
            for path in inno_paths:
                if Path(path).exists() or shutil.which(path):
                    inno_exe = path
                    break

            if not inno_exe:
                self.logger.warning("Inno Setup not found, skipping installer creation")
                return False

            result = subprocess.run([inno_exe, str(iss_file)],
                                  capture_output=True, text=True)

            if result.returncode == 0:
                self.logger.info("Windows installer created successfully")
                return True
            else:
                self.logger.error(f"Inno Setup failed: {result.stderr}")
                return False

        except Exception as e:
            self.logger.error(f"Installer creation failed: {e}")
            return False

    def _get_inno_setup_script(self) -> str:
        """Generate Inno Setup script"""
        app_name = self.config.config["app_name"]
        app_version = self.config.config["app_version"]
        app_author = self.config.config["app_author"]

        return f'''[Setup]
AppName={app_name}
AppVersion={app_version}
AppPublisher={app_author}
DefaultDirName={{autopf}}\\{app_name}
DefaultGroupName={app_name}
OutputDir=dist\\installer
OutputBaseFilename={app_name.replace(" ", "_")}_Setup_{app_version}
Compression=lzma
SolidCompression=yes
ArchitecturesAllowed=x64
ArchitecturesInstallIn64BitMode=x64
SetupIconFile={self.config.config["app_icon"]}
UninstallDisplayIcon={{app}}\\{app_name.replace(" ", "_")}.exe

[Languages]
Name: "english"; MessagesFile: "compiler:Default.isl"

[Tasks]
Name: "desktopicon"; Description: "{{cm:CreateDesktopIcon}}"; GroupDescription: "{{cm:AdditionalIcons}}"; Flags: unchecked
Name: "quicklaunchicon"; Description: "{{cm:CreateQuickLaunchIcon}}"; GroupDescription: "{{cm:AdditionalIcons}}"; Flags: unchecked; OnlyBelowVersion: 6.1

[Files]
Source: "dist\\{app_name.replace(" ", "_")}\\*"; DestDir: "{{app}}"; Flags: ignoreversion recursesubdirs createallsubdirs

[Icons]
Name: "{{group}}\\{app_name}"; Filename: "{{app}}\\{app_name.replace(" ", "_")}.exe"
Name: "{{autodesktop}}\\{app_name}"; Filename: "{{app}}\\{app_name.replace(" ", "_")}.exe"; Tasks: desktopicon
Name: "{{userappdata}}\\Microsoft\\Internet Explorer\\Quick Launch\\{app_name}"; Filename: "{{app}}\\{app_name.replace(" ", "_")}.exe"; Tasks: quicklaunchicon

[Run]
Filename: "{{app}}\\{app_name.replace(" ", "_")}.exe"; Description: "{{cm:LaunchProgram,{app_name}}}"; Flags: nowait postinstall skipifsilent

[UninstallDelete]
Type: filesandordirs; Name: "{{app}}"
'''

    def create_macos_bundle(self) -> bool:
        """Create macOS application bundle"""
        if self.config.platform != "darwin":
            return True

        app_name = self.config.config["app_name"]
        app_bundle = Path(f"dist/{app_name}.app")

        try:
            # Create bundle structure
            contents_dir = app_bundle / "Contents"
            macos_dir = contents_dir / "MacOS"
            resources_dir = contents_dir / "Resources"

            for dir_path in [contents_dir, macos_dir, resources_dir]:
                dir_path.mkdir(parents=True, exist_ok=True)

            # Copy executable
            exe_src = Path(f"dist/{app_name.replace(' ', '_')}")
            exe_dst = macos_dir / app_name.replace(' ', '_')
            shutil.copy2(exe_src, exe_dst)
            exe_dst.chmod(0o755)

            # Create Info.plist
            plist_content = self._get_macos_plist()
            with open(contents_dir / "Info.plist", "w") as f:
                f.write(plist_content)

            # Copy icon if available
            icon_path = Path(self.config.config["app_icon"])
            if icon_path.exists() and icon_path.suffix.lower() == '.icns':
                shutil.copy2(icon_path, resources_dir / "icon.icns")

            self.logger.info("macOS bundle created successfully")
            return True

        except Exception as e:
            self.logger.error(f"macOS bundle creation failed: {e}")
            return False

    def _get_macos_plist(self) -> str:
        """Generate macOS Info.plist"""
        app_name = self.config.config["app_name"]
        app_version = self.config.config["app_version"]

        return f'''<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>CFBundleExecutable</key>
    <string>{app_name.replace(' ', '_')}</string>
    <key>CFBundleIdentifier</key>
    <string>com.yourcompany.{app_name.lower().replace(' ', '')}</string>
    <key>CFBundleName</key>
    <string>{app_name}</string>
    <key>CFBundleVersion</key>
    <string>{app_version}</string>
    <key>CFBundleShortVersionString</key>
    <string>{app_version}</string>
    <key>CFBundleIconFile</key>
    <string>icon.icns</string>
    <key>CFBundlePackageType</key>
    <string>APPL</string>
    <key>CFBundleSignature</key>
    <string>????</string>
    <key>LSMinimumSystemVersion</key>
    <string>10.13</string>
    <key>NSHighResolutionCapable</key>
    <true/>
</dict>
</plist>'''

    def create_linux_packages(self) -> bool:
        """Create Linux distribution packages"""
        if self.config.platform != "linux":
            return True

        success = True

        # Create AppImage
        if not self._create_appimage():
            success = False

        # Create DEB package
        if not self._create_deb_package():
            success = False

        return success

    def _create_appimage(self) -> bool:
        """Create AppImage for Linux"""
        try:
            app_name = self.config.config["app_name"]
            appdir = Path(f"dist/{app_name}.AppDir")

            # Create AppDir structure
            usr_bin = appdir / "usr" / "bin"
            usr_share = appdir / "usr" / "share"
            usr_share.mkdir(parents=True, exist_ok=True)
            usr_bin.mkdir(parents=True, exist_ok=True)

            # Copy executable
            exe_src = Path(f"dist/{app_name.replace(' ', '_')}")
            exe_dst = usr_bin / app_name.replace(' ', '_')
            shutil.copy2(exe_src, exe_dst)
            exe_dst.chmod(0o755)

            # Create AppRun
            apprun_content = f'''#!/bin/bash
SELF=$(readlink -f "$0")
HERE=${{SELF%/*}}
EXEC="${{HERE}}/usr/bin/{app_name.replace(' ', '_')}"
exec "${{EXEC}}" "$@"
'''
            with open(appdir / "AppRun", "w") as f:
                f.write(apprun_content)
            (appdir / "AppRun").chmod(0o755)

            # Create desktop file
            desktop_content = f'''[Desktop Entry]
Type=Application
Name={app_name}
Exec={app_name.replace(' ', '_')}
Icon={app_name.lower().replace(' ', '')}
Categories=Utility;
'''
            with open(appdir / f"{app_name.replace(' ', '')}.desktop", "w") as f:
                f.write(desktop_content)

            self.logger.info("AppImage directory created successfully")
            return True

        except Exception as e:
            self.logger.error(f"AppImage creation failed: {e}")
            return False

    def build_all_platforms(self):
        """Build for all target platforms"""
        self.logger.info("Starting cross-platform build process")

        # Clean previous builds
        self.clean_build()

        # Build executable
        if not self.build_executable():
            self.logger.error("Executable build failed")
            return False

        # Platform-specific packaging
        if self.config.platform == "windows":
            self.create_windows_installer()
        elif self.config.platform == "darwin":
            self.create_macos_bundle()
        elif self.config.platform == "linux":
            self.create_linux_packages()

        self.logger.info("Build process completed")
        return True

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)

    config = BuildConfig()
    builder = DesktopAppBuilder(config)
    builder.build_all_platforms()
```

### C++ Cross-Platform Deployment

**Use when copilot.instructions.md specifies: C++, wxWidgets, CMake**

```cmake
# CMakeLists.txt - Cross-platform build configuration
cmake_minimum_required(VERSION 3.16)
project(DesktopApplication VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Package information
set(CPACK_PACKAGE_NAME "Desktop Application")
set(CPACK_PACKAGE_VERSION_MAJOR 1)
set(CPACK_PACKAGE_VERSION_MINOR 0)
set(CPACK_PACKAGE_VERSION_PATCH 0)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Desktop application built with C++ and wxWidgets")
set(CPACK_PACKAGE_VENDOR "Your Company")
set(CPACK_PACKAGE_CONTACT "contact@yourcompany.com")

# Find required packages
find_package(wxWidgets REQUIRED COMPONENTS core base)
find_package(SQLite3 REQUIRED)

if(wxWidgets_FOUND)
    include(${wxWidgets_USE_FILE})
endif()

# Include directories
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/src
)

# Source files
file(GLOB_RECURSE SOURCES
    "src/*.cpp"
    "src/*.h"
    "include/*.h"
)

# Exclude platform-specific files
if(NOT WIN32)
    list(FILTER SOURCES EXCLUDE REGEX ".*windows.*")
endif()

if(NOT APPLE)
    list(FILTER SOURCES EXCLUDE REGEX ".*macos.*")
endif()

if(NOT UNIX OR APPLE)
    list(FILTER SOURCES EXCLUDE REGEX ".*linux.*")
endif()

# Create executable
if(WIN32)
    add_executable(${PROJECT_NAME} WIN32 ${SOURCES})

    # Windows-specific settings
    set_target_properties(${PROJECT_NAME} PROPERTIES
        VS_DPI_AWARE "PerMonitor"
        WIN32_EXECUTABLE TRUE
    )

    # Windows resources
    if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/resources/app.rc")
        target_sources(${PROJECT_NAME} PRIVATE resources/app.rc)
    endif()

elseif(APPLE)
    add_executable(${PROJECT_NAME} MACOSX_BUNDLE ${SOURCES})

    # macOS-specific settings
    set_target_properties(${PROJECT_NAME} PROPERTIES
        MACOSX_BUNDLE TRUE
        MACOSX_BUNDLE_GUI_IDENTIFIER "com.yourcompany.desktopapp"
        MACOSX_BUNDLE_BUNDLE_NAME "Desktop Application"
        MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
        MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION}
        MACOSX_BUNDLE_COPYRIGHT "© Your Company"
    )

    # macOS icon
    if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/resources/app.icns")
        set_target_properties(${PROJECT_NAME} PROPERTIES
            MACOSX_BUNDLE_ICON_FILE app.icns
        )
        set_source_files_properties(resources/app.icns PROPERTIES
            MACOSX_PACKAGE_LOCATION Resources
        )
        target_sources(${PROJECT_NAME} PRIVATE resources/app.icns)
    endif()

else()
    add_executable(${PROJECT_NAME} ${SOURCES})
endif()

# Link libraries
target_link_libraries(${PROJECT_NAME}
    ${wxWidgets_LIBRARIES}
    SQLite::SQLite3
)

# Compiler-specific settings
if(MSVC)
    target_compile_options(${PROJECT_NAME} PRIVATE /W4)
    # Static linking for Windows
    set_property(TARGET ${PROJECT_NAME} PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
else()
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -pedantic)
endif()

# Installation settings
if(WIN32)
    install(TARGETS ${PROJECT_NAME}
        DESTINATION .
    )

    # Install Visual C++ Redistributables
    include(InstallRequiredSystemLibraries)

    # Windows installer with NSIS
    set(CPACK_GENERATOR "NSIS")
    set(CPACK_NSIS_DISPLAY_NAME "Desktop Application")
    set(CPACK_NSIS_PACKAGE_NAME "Desktop Application")
    set(CPACK_NSIS_HELP_LINK "https://yourcompany.com/support")
    set(CPACK_NSIS_URL_INFO_ABOUT "https://yourcompany.com")
    set(CPACK_NSIS_CONTACT "contact@yourcompany.com")
    set(CPACK_NSIS_MODIFY_PATH ON)
    set(CPACK_NSIS_ENABLE_UNINSTALL_BEFORE_INSTALL ON)

    # Desktop shortcut
    set(CPACK_NSIS_CREATE_ICONS_EXTRA
        "CreateShortCut '$DESKTOP\\\\Desktop Application.lnk' '$INSTDIR\\\\${PROJECT_NAME}.exe'"
    )

    set(CPACK_NSIS_DELETE_ICONS_EXTRA
        "Delete '$DESKTOP\\\\Desktop Application.lnk'"
    )

elseif(APPLE)
    install(TARGETS ${PROJECT_NAME}
        BUNDLE DESTINATION .
    )

    # macOS Bundle
    set(CPACK_GENERATOR "DragNDrop")
    set(CPACK_DMG_FORMAT "UDBZ")
    set(CPACK_DMG_VOLUME_NAME "Desktop Application")
    set(CPACK_DMG_DS_STORE "${CMAKE_CURRENT_SOURCE_DIR}/resources/DS_Store")
    set(CPACK_DMG_BACKGROUND_IMAGE "${CMAKE_CURRENT_SOURCE_DIR}/resources/dmg_background.png")

else()
    install(TARGETS ${PROJECT_NAME}
        RUNTIME DESTINATION bin
    )

    # Linux packages
    set(CPACK_GENERATOR "DEB;RPM;TGZ")

    # DEB package settings
    set(CPACK_DEBIAN_PACKAGE_DEPENDS "libwxgtk3.0-gtk3-0v5, libsqlite3-0")
    set(CPACK_DEBIAN_PACKAGE_SECTION "utils")
    set(CPACK_DEBIAN_PACKAGE_PRIORITY "optional")
    set(CPACK_DEBIAN_PACKAGE_HOMEPAGE "https://yourcompany.com")

    # RPM package settings
    set(CPACK_RPM_PACKAGE_GROUP "Applications/Productivity")
    set(CPACK_RPM_PACKAGE_LICENSE "MIT")
    set(CPACK_RPM_PACKAGE_URL "https://yourcompany.com")
    set(CPACK_RPM_PACKAGE_REQUIRES "wxGTK3-devel, sqlite-devel")

    # Install desktop file
    install(FILES resources/desktopapp.desktop
        DESTINATION share/applications
    )

    # Install icon
    install(FILES resources/app.png
        DESTINATION share/icons/hicolor/256x256/apps
        RENAME desktopapp.png
    )
endif()

# Resource files
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/resources")
    install(DIRECTORY resources/
        DESTINATION resources
        PATTERN "*.rc" EXCLUDE
        PATTERN "*.icns" EXCLUDE
    )
endif()

# Documentation
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/README.md")
    install(FILES README.md LICENSE
        DESTINATION docs
    )
endif()

# Enable CPack
include(CPack)

# Custom targets for development
add_custom_target(run
    COMMAND ${PROJECT_NAME}
    DEPENDS ${PROJECT_NAME}
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Running the application"
)

add_custom_target(install-local
    COMMAND ${CMAKE_COMMAND} --build . --target install
    DEPENDS ${PROJECT_NAME}
    COMMENT "Installing locally"
)

# Platform-specific post-build steps
if(WIN32)
    # Copy wxWidgets DLLs for development
    add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
        $<TARGET_FILE:${wxWidgets_LIBRARIES}>
        $<TARGET_FILE_DIR:${PROJECT_NAME}>
        COMMENT "Copying wxWidgets DLLs"
    )
endif()
```

```bash
#!/bin/bash
# build_scripts/build.sh - Cross-platform build script

set -e

# Configuration
APP_NAME="Desktop Application"
VERSION="1.0.0"
BUILD_TYPE="Release"

# Colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m' # No Color

log_info() {
    echo -e "${GREEN}[INFO]${NC} $1"
}

log_warn() {
    echo -e "${YELLOW}[WARN]${NC} $1"
}

log_error() {
    echo -e "${RED}[ERROR]${NC} $1"
}

# Detect platform
PLATFORM=$(uname -s)
case $PLATFORM in
    Linux*)     PLATFORM=Linux;;
    Darwin*)    PLATFORM=macOS;;
    CYGWIN*|MINGW*|MSYS*) PLATFORM=Windows;;
    *)          PLATFORM="Unknown";;
esac

log_info "Building for platform: $PLATFORM"

# Create build directory
BUILD_DIR="build-$PLATFORM"
if [ -d "$BUILD_DIR" ]; then
    log_warn "Removing existing build directory"
    rm -rf "$BUILD_DIR"
fi

mkdir -p "$BUILD_DIR"
cd "$BUILD_DIR"

# Configure build
log_info "Configuring CMake..."

CMAKE_ARGS="-DCMAKE_BUILD_TYPE=$BUILD_TYPE"

case $PLATFORM in
    Windows)
        CMAKE_ARGS="$CMAKE_ARGS -G \"Visual Studio 16 2019\" -A x64"
        ;;
    macOS)
        CMAKE_ARGS="$CMAKE_ARGS -DCMAKE_OSX_MINIMUM_VERSION=10.13"
        ;;
    Linux)
        CMAKE_ARGS="$CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=/usr"
        ;;
esac

eval "cmake $CMAKE_ARGS .."

# Build
log_info "Building application..."
cmake --build . --config $BUILD_TYPE --parallel $(nproc 2>/dev/null || sysctl -n hw.ncpu 2>/dev/null || echo 4)

# Package
log_info "Creating packages..."
case $PLATFORM in
    Windows)
        cpack -G NSIS
        ;;
    macOS)
        cpack -G DragNDrop
        ;;
    Linux)
        cpack -G DEB
        cpack -G RPM
        cpack -G TGZ
        ;;
esac

# Show results
log_info "Build completed successfully!"
log_info "Packages created in: $(pwd)"
ls -la *.exe *.dmg *.deb *.rpm *.tar.gz 2>/dev/null || true

cd ..
```

### .NET Desktop Application Deployment

**Use when copilot.instructions.md specifies: C#, .NET, WPF/WinForms**

```xml
<!-- Directory.Build.props - Global project properties -->
<Project>
  <PropertyGroup>
    <TargetFramework>net6.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>

    <!-- Application Information -->
    <AssemblyTitle>Desktop Application</AssemblyTitle>
    <AssemblyDescription>Desktop application built with .NET and WPF</AssemblyDescription>
    <AssemblyCompany>Your Company</AssemblyCompany>
    <AssemblyCopyright>© Your Company</AssemblyCopyright>
    <AssemblyVersion>1.0.0.0</AssemblyVersion>
    <FileVersion>1.0.0.0</FileVersion>
    <ProductVersion>1.0.0</ProductVersion>

    <!-- Publishing Settings -->
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
    <IncludeNativeLibrariesForSelfExtract>true</IncludeNativeLibrariesForSelfExtract>

    <!-- Icon and Manifest -->
    <ApplicationIcon>Assets\app.ico</ApplicationIcon>
    <ApplicationManifest>app.manifest</ApplicationManifest>
  </PropertyGroup>

  <ItemGroup Condition="'$(TargetFramework)' == 'net6.0-windows'">
    <PackageReference Include="Microsoft.WindowsAppSDK" Version="1.4.231008000" />
    <PackageReference Include="Microsoft.Windows.SDK.BuildTools" Version="10.0.22621.2428" />
  </ItemGroup>
</Project>
```

```powershell
# build_scripts/Build-Application.ps1 - PowerShell build script
param(
    [string]$Configuration = "Release",
    [string]$Platform = "x64",
    [string]$OutputPath = "dist",
    [switch]$CreateInstaller = $false,
    [switch]$SignBinaries = $false
)

# Configuration
$AppName = "Desktop Application"
$Version = "1.0.0"
$Publisher = "Your Company"

Write-Host "Building $AppName v$Version" -ForegroundColor Green
Write-Host "Configuration: $Configuration" -ForegroundColor Yellow
Write-Host "Platform: $Platform" -ForegroundColor Yellow

# Clean previous builds
if (Test-Path $OutputPath) {
    Remove-Item -Recurse -Force $OutputPath
    Write-Host "Cleaned previous build artifacts" -ForegroundColor Yellow
}

New-Item -ItemType Directory -Path $OutputPath -Force | Out-Null

# Build for different runtimes
$runtimes = @("win-x64", "win-x86", "win-arm64")

foreach ($runtime in $runtimes) {
    Write-Host "Building for runtime: $runtime" -ForegroundColor Cyan

    $publishPath = "$OutputPath\$runtime"

    # Publish application
    $publishArgs = @(
        "publish"
        "--configuration", $Configuration
        "--runtime", $runtime
        "--output", $publishPath
        "--self-contained", "true"
        "--publish-single-file", "true"
        "--publish-trimmed", "true"
        "--publish-ready-to-run", "true"
        "/p:IncludeNativeLibrariesForSelfExtract=true"
        "/p:PublishSingleFile=true"
        "/p:Version=$Version"
    )

    & dotnet @publishArgs

    if ($LASTEXITCODE -ne 0) {
        Write-Error "Build failed for runtime $runtime"
        exit 1
    }

    # Sign binaries if requested
    if ($SignBinaries -and (Get-Command "signtool.exe" -ErrorAction SilentlyContinue)) {
        Write-Host "Signing binaries for $runtime" -ForegroundColor Yellow

        $exePath = Get-ChildItem "$publishPath\*.exe" | Select-Object -First 1
        if ($exePath) {
            & signtool.exe sign /fd SHA256 /t http://timestamp.digicert.com $exePath.FullName
        }
    }

    # Create ZIP archive
    $zipPath = "$OutputPath\$AppName-$Version-$runtime.zip"
    Compress-Archive -Path "$publishPath\*" -DestinationPath $zipPath -Force
    Write-Host "Created archive: $zipPath" -ForegroundColor Green
}

Write-Host "`nBuild completed successfully!" -ForegroundColor Green
Write-Host "Output directory: $OutputPath" -ForegroundColor Yellow
Get-ChildItem $OutputPath -Recurse -Include "*.exe", "*.zip", "*.msi" | Select-Object Name, Length, LastWriteTime
```

## Quality Gates

### ✅ Deployment Compliance
- [ ] Deployment approach matches copilot.instructions.md technology specification
- [ ] Target platforms correctly identified and supported
- [ ] Platform-specific packaging implemented
- [ ] Installation/uninstallation tested on target platforms

### ✅ Distribution Quality
- [ ] Application signed for security (where applicable)
- [ ] Auto-update mechanism implemented
- [ ] Dependency management handled correctly
- [ ] Installation size optimized

### ✅ User Experience
- [ ] Professional installation experience
- [ ] Desktop shortcuts and menu entries created
- [ ] Uninstallation removes all components
- [ ] Application launches correctly after installation

## Transition to Specialized Chatmodes

After completing desktop deployment and packaging:

- **For Distribution Setup**: Switch to **deployment-engineer** chatmode to implement CI/CD pipelines for automated releases
- **For Security Enhancement**: Switch to **security-engineer** chatmode to implement code signing and security validation
- **For Quality Assurance**: Switch to **qa-engineer** chatmode to implement automated testing for deployment packages

**This prompt ensures desktop applications are packaged and deployed using appropriate methods for the technology stack and target platforms specified in copilot.instructions.md, providing professional distribution packages.**