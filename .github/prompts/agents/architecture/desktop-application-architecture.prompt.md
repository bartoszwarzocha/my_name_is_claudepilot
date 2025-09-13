---
description: Design comprehensive desktop application architecture that adapts to the technology stack, implementing appropriate architectural patterns, separation of concerns, and maintainable code structure for desktop applications.
tools:
  - codebase
  - search
  - editFiles
  - runCommands
model: claude-4-sonnet
---

# Desktop Application Architecture Design

## Mission
Design comprehensive desktop application architecture that adapts to the technology stack defined in copilot.instructions.md, implementing appropriate architectural patterns, separation of concerns, and maintainable code structure for desktop applications.

## Pre-Implementation Analysis

### Step 1: Project Technology Detection
**CRITICAL: Always analyze copilot.instructions.md first to determine the desktop technology stack:**

Read project configuration to identify:
- **primary_language** field (Python, C++, C#, Java, JavaScript)
- **Frontend technologies** for desktop framework selection
- **Desktop platform requirements** (Windows, macOS, Linux, cross-platform)

**Technology-specific project analysis:**
```bash
# For Python/wxPython
find . -name "*.py" -o -name "requirements.txt" | head -5
ls -la src/ ui/ models/ controllers/ 2>/dev/null

# For C++/wxWidgets
find . -name "*.cpp" -o -name "*.h" -o -name "CMakeLists.txt" | head -5
ls -la src/ include/ ui/ 2>/dev/null

# For .NET/WPF/WinForms
find . -name "*.csproj" -o -name "*.xaml" -o -name "*.cs" | head -5
ls -la Views/ ViewModels/ Models/ Controllers/ 2>/dev/null

# For Java/Swing/JavaFX
find . -name "*.java" -o -name "pom.xml" -o -name "*.fxml" | head -5
ls -la src/main/java/ 2>/dev/null

# For Electron/Node.js
find . -name "package.json" -o -name "*.js" -o -name "*.ts" | head -5
ls -la src/ main/ renderer/ 2>/dev/null
```

### Step 2: Existing Project Structure Analysis
```bash
# Universal desktop project analysis
tree . -I "node_modules|bin|obj|target|dist|build|__pycache__" -L 3
find . -type f -name "*.md" | grep -i readme | head -3
```

## Technology-Specific Architecture Patterns

**⚠️ IMPORTANT: Select architecture pattern based on copilot.instructions.md desktop technology configuration**

### Python/wxPython Architecture

**Use when copilot.instructions.md specifies: Python, wxPython, desktop**

```python
# main.py - Application entry point
import wx
from controllers.main_controller import MainController
from models.app_model import AppModel
from views.main_view import MainView

class DesktopApp(wx.App):
    def OnInit(self):
        # Initialize Model-View-Controller architecture
        self.model = AppModel()
        self.controller = MainController(self.model)
        self.main_view = MainView(None, self.controller)
        
        self.main_view.Show()
        self.SetTopWindow(self.main_view)
        return True

if __name__ == '__main__':
    app = DesktopApp()
    app.MainLoop()
```

```python
# models/app_model.py - Data and business logic layer
from typing import List, Optional
from dataclasses import dataclass
import sqlite3
import logging

@dataclass
class Entity:
    id: Optional[int] = None
    name: str = ""
    created_at: Optional[str] = None

class AppModel:
    def __init__(self, db_path: str = "app_data.db"):
        self.db_path = db_path
        self.logger = logging.getLogger(__name__)
        self._observers = []
        self.init_database()
    
    def init_database(self):
        """Initialize database schema"""
        with sqlite3.connect(self.db_path) as conn:
            conn.execute('''
                CREATE TABLE IF NOT EXISTS entities (
                    id INTEGER PRIMARY KEY AUTOINCREMENT,
                    name TEXT NOT NULL,
                    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
                )
            ''')
            conn.commit()
    
    def add_observer(self, observer):
        """Observer pattern for view updates"""
        self._observers.append(observer)
    
    def notify_observers(self, event_type: str, data=None):
        """Notify all observers of model changes"""
        for observer in self._observers:
            observer.model_changed(event_type, data)
    
    def get_entities(self) -> List[Entity]:
        """Retrieve all entities"""
        try:
            with sqlite3.connect(self.db_path) as conn:
                cursor = conn.execute("SELECT id, name, created_at FROM entities")
                return [Entity(id=row[0], name=row[1], created_at=row[2]) 
                       for row in cursor.fetchall()]
        except Exception as e:
            self.logger.error(f"Error retrieving entities: {e}")
            return []
    
    def add_entity(self, entity: Entity) -> bool:
        """Add new entity"""
        try:
            with sqlite3.connect(self.db_path) as conn:
                cursor = conn.execute(
                    "INSERT INTO entities (name) VALUES (?)",
                    (entity.name,)
                )
                entity.id = cursor.lastrowid
                conn.commit()
                self.notify_observers('entity_added', entity)
                return True
        except Exception as e:
            self.logger.error(f"Error adding entity: {e}")
            return False
```

```python
# controllers/main_controller.py - Business logic coordinator
from typing import Optional
import logging
from models.app_model import AppModel, Entity

class MainController:
    def __init__(self, model: AppModel):
        self.model = model
        self.logger = logging.getLogger(__name__)
    
    def handle_add_entity(self, name: str) -> bool:
        """Handle entity addition with validation"""
        if not name.strip():
            self.logger.warning("Attempted to add entity with empty name")
            return False
        
        entity = Entity(name=name.strip())
        return self.model.add_entity(entity)
    
    def handle_get_entities(self):
        """Handle entity retrieval"""
        return self.model.get_entities()
    
    def handle_delete_entity(self, entity_id: int) -> bool:
        """Handle entity deletion"""
        return self.model.delete_entity(entity_id)
    
    def validate_input(self, input_data: dict) -> tuple[bool, str]:
        """Validate user input"""
        if 'name' not in input_data:
            return False, "Name is required"
        
        if len(input_data['name'].strip()) < 2:
            return False, "Name must be at least 2 characters"
        
        return True, ""
```

```python
# views/main_view.py - User interface layer
import wx
from typing import Optional
import logging

class MainView(wx.Frame):
    def __init__(self, parent, controller):
        super().__init__(parent, title="Desktop Application", size=(800, 600))
        self.controller = controller
        self.logger = logging.getLogger(__name__)
        
        # Register as observer for model changes
        self.controller.model.add_observer(self)
        
        self.init_ui()
        self.bind_events()
        self.refresh_data()
    
    def init_ui(self):
        """Initialize user interface components"""
        # Main panel
        self.panel = wx.Panel(self)
        
        # Create menu bar
        self.create_menu_bar()
        
        # Create toolbar
        self.create_toolbar()
        
        # Main sizer
        main_sizer = wx.BoxSizer(wx.VERTICAL)
        
        # Input section
        input_sizer = wx.BoxSizer(wx.HORIZONTAL)
        self.name_input = wx.TextCtrl(self.panel, size=(300, -1))
        add_btn = wx.Button(self.panel, label="Add Entity")
        
        input_sizer.Add(wx.StaticText(self.panel, label="Name:"), 0, 
                       wx.ALIGN_CENTER_VERTICAL | wx.RIGHT, 5)
        input_sizer.Add(self.name_input, 0, wx.RIGHT, 5)
        input_sizer.Add(add_btn, 0)
        
        # List control
        self.entity_list = wx.ListCtrl(self.panel, style=wx.LC_REPORT | wx.LC_SINGLE_SEL)
        self.entity_list.AppendColumn("ID", width=80)
        self.entity_list.AppendColumn("Name", width=200)
        self.entity_list.AppendColumn("Created", width=150)
        
        # Layout
        main_sizer.Add(input_sizer, 0, wx.ALL | wx.EXPAND, 10)
        main_sizer.Add(self.entity_list, 1, wx.ALL | wx.EXPAND, 10)
        
        self.panel.SetSizer(main_sizer)
        
        # Status bar
        self.CreateStatusBar()
        self.SetStatusText("Ready")
        
        # Bind events
        add_btn.Bind(wx.EVT_BUTTON, self.on_add_entity)
        self.name_input.Bind(wx.EVT_TEXT_ENTER, self.on_add_entity)
    
    def create_menu_bar(self):
        """Create application menu bar"""
        menubar = wx.MenuBar()
        
        # File menu
        file_menu = wx.Menu()
        file_menu.Append(wx.ID_NEW, "&New\tCtrl+N", "Create new item")
        file_menu.AppendSeparator()
        file_menu.Append(wx.ID_EXIT, "&Exit\tCtrl+Q", "Exit application")
        
        # Edit menu
        edit_menu = wx.Menu()
        edit_menu.Append(wx.ID_DELETE, "&Delete\tDel", "Delete selected item")
        
        menubar.Append(file_menu, "&File")
        menubar.Append(edit_menu, "&Edit")
        
        self.SetMenuBar(menubar)
        
        # Bind menu events
        self.Bind(wx.EVT_MENU, self.on_add_entity, id=wx.ID_NEW)
        self.Bind(wx.EVT_MENU, self.on_exit, id=wx.ID_EXIT)
        self.Bind(wx.EVT_MENU, self.on_delete_entity, id=wx.ID_DELETE)
    
    def create_toolbar(self):
        """Create application toolbar"""
        toolbar = self.CreateToolBar()
        toolbar.AddTool(wx.ID_NEW, "New", wx.ArtProvider.GetBitmap(wx.ART_NEW))
        toolbar.AddTool(wx.ID_DELETE, "Delete", wx.ArtProvider.GetBitmap(wx.ART_DELETE))
        toolbar.Realize()
    
    def bind_events(self):
        """Bind additional events"""
        self.Bind(wx.EVT_CLOSE, self.on_close)
    
    def on_add_entity(self, event):
        """Handle add entity event"""
        name = self.name_input.GetValue()
        
        # Validate input
        is_valid, error_message = self.controller.validate_input({'name': name})
        if not is_valid:
            wx.MessageBox(error_message, "Validation Error", wx.OK | wx.ICON_ERROR)
            return
        
        # Add entity
        if self.controller.handle_add_entity(name):
            self.name_input.Clear()
            self.SetStatusText("Entity added successfully")
        else:
            wx.MessageBox("Failed to add entity", "Error", wx.OK | wx.ICON_ERROR)
    
    def on_delete_entity(self, event):
        """Handle delete entity event"""
        selected = self.entity_list.GetFirstSelected()
        if selected == -1:
            wx.MessageBox("Please select an entity to delete", "No Selection", 
                         wx.OK | wx.ICON_INFORMATION)
            return
        
        entity_id = int(self.entity_list.GetItemText(selected, 0))
        
        if wx.MessageBox("Are you sure you want to delete this entity?", "Confirm Delete",
                        wx.YES_NO | wx.ICON_QUESTION) == wx.YES:
            if self.controller.handle_delete_entity(entity_id):
                self.SetStatusText("Entity deleted successfully")
            else:
                wx.MessageBox("Failed to delete entity", "Error", wx.OK | wx.ICON_ERROR)
    
    def on_exit(self, event):
        """Handle application exit"""
        self.Close()
    
    def on_close(self, event):
        """Handle window close event"""
        self.Destroy()
    
    def model_changed(self, event_type: str, data=None):
        """Handle model change notifications"""
        if event_type in ['entity_added', 'entity_deleted', 'entity_updated']:
            self.refresh_data()
    
    def refresh_data(self):
        """Refresh data display"""
        self.entity_list.DeleteAllItems()
        entities = self.controller.handle_get_entities()
        
        for entity in entities:
            index = self.entity_list.InsertItem(self.entity_list.GetItemCount(), str(entity.id))
            self.entity_list.SetItem(index, 1, entity.name)
            self.entity_list.SetItem(index, 2, entity.created_at or "")
```

### C++/wxWidgets Architecture

**Use when copilot.instructions.md specifies: C++, wxWidgets, desktop**

```cpp
// src/main.cpp - Application entry point
#include <wx/wx.h>
#include "controllers/MainController.h"
#include "models/AppModel.h"
#include "views/MainView.h"

class DesktopApp : public wxApp {
public:
    virtual bool OnInit() override {
        // Initialize Model-View-Controller architecture
        model = std::make_shared<AppModel>();
        controller = std::make_unique<MainController>(model);
        
        MainView* mainView = new MainView(controller.get());
        mainView->Show(true);
        
        return true;
    }

private:
    std::shared_ptr<AppModel> model;
    std::unique_ptr<MainController> controller;
};

wxIMPLEMENT_APP(DesktopApp);
```

```cpp
// include/models/AppModel.h - Data and business logic layer
#pragma once
#include <vector>
#include <memory>
#include <functional>
#include <sqlite3.h>
#include <string>

struct Entity {
    int id = 0;
    std::string name;
    std::string created_at;
    
    Entity(const std::string& n = "") : name(n) {}
};

class AppModel {
public:
    using Observer = std::function<void(const std::string&, const Entity*)>;
    
    AppModel(const std::string& db_path = "app_data.db");
    ~AppModel();
    
    // Observer pattern
    void AddObserver(Observer observer);
    void NotifyObservers(const std::string& event_type, const Entity* data = nullptr);
    
    // Data operations
    std::vector<Entity> GetEntities();
    bool AddEntity(const Entity& entity);
    bool DeleteEntity(int entity_id);
    bool UpdateEntity(const Entity& entity);

private:
    sqlite3* db;
    std::vector<Observer> observers;
    std::string db_path;
    
    void InitDatabase();
    void LogError(const std::string& message);
};
```

```cpp
// src/models/AppModel.cpp
#include "models/AppModel.h"
#include <iostream>
#include <sstream>

AppModel::AppModel(const std::string& db_path) : db_path(db_path), db(nullptr) {
    InitDatabase();
}

AppModel::~AppModel() {
    if (db) {
        sqlite3_close(db);
    }
}

void AppModel::InitDatabase() {
    int rc = sqlite3_open(db_path.c_str(), &db);
    if (rc != SQLITE_OK) {
        LogError("Cannot open database: " + std::string(sqlite3_errmsg(db)));
        return;
    }
    
    const char* sql = R"(
        CREATE TABLE IF NOT EXISTS entities (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL,
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );
    )";
    
    char* err_msg = nullptr;
    rc = sqlite3_exec(db, sql, nullptr, nullptr, &err_msg);
    if (rc != SQLITE_OK) {
        LogError("SQL error: " + std::string(err_msg));
        sqlite3_free(err_msg);
    }
}

void AppModel::AddObserver(Observer observer) {
    observers.push_back(observer);
}

void AppModel::NotifyObservers(const std::string& event_type, const Entity* data) {
    for (const auto& observer : observers) {
        observer(event_type, data);
    }
}

std::vector<Entity> AppModel::GetEntities() {
    std::vector<Entity> entities;
    
    const char* sql = "SELECT id, name, created_at FROM entities ORDER BY created_at DESC";
    sqlite3_stmt* stmt;
    
    int rc = sqlite3_prepare_v2(db, sql, -1, &stmt, nullptr);
    if (rc != SQLITE_OK) {
        LogError("Failed to prepare statement: " + std::string(sqlite3_errmsg(db)));
        return entities;
    }
    
    while ((rc = sqlite3_step(stmt)) == SQLITE_ROW) {
        Entity entity;
        entity.id = sqlite3_column_int(stmt, 0);
        entity.name = reinterpret_cast<const char*>(sqlite3_column_text(stmt, 1));
        entity.created_at = reinterpret_cast<const char*>(sqlite3_column_text(stmt, 2));
        entities.push_back(entity);
    }
    
    sqlite3_finalize(stmt);
    return entities;
}

bool AppModel::AddEntity(const Entity& entity) {
    const char* sql = "INSERT INTO entities (name) VALUES (?)";
    sqlite3_stmt* stmt;
    
    int rc = sqlite3_prepare_v2(db, sql, -1, &stmt, nullptr);
    if (rc != SQLITE_OK) {
        LogError("Failed to prepare statement: " + std::string(sqlite3_errmsg(db)));
        return false;
    }
    
    sqlite3_bind_text(stmt, 1, entity.name.c_str(), -1, SQLITE_STATIC);
    
    rc = sqlite3_step(stmt);
    sqlite3_finalize(stmt);
    
    if (rc == SQLITE_DONE) {
        Entity added_entity = entity;
        added_entity.id = static_cast<int>(sqlite3_last_insert_rowid(db));
        NotifyObservers("entity_added", &added_entity);
        return true;
    }
    
    LogError("Failed to insert entity: " + std::string(sqlite3_errmsg(db)));
    return false;
}

void AppModel::LogError(const std::string& message) {
    std::cerr << "AppModel Error: " << message << std::endl;
}
```

### .NET/WPF MVVM Architecture

**Use when copilot.instructions.md specifies: C#, .NET, WPF, desktop**

```csharp
// App.xaml.cs - Application entry point
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using System.Windows;

namespace DesktopApp
{
    public partial class App : Application
    {
        private IHost _host;

        protected override void OnStartup(StartupEventArgs e)
        {
            _host = Host.CreateDefaultBuilder()
                .ConfigureServices((context, services) =>
                {
                    // Register services
                    services.AddSingleton<IAppModel, AppModel>();
                    services.AddTransient<MainViewModel>();
                    services.AddTransient<MainWindow>();
                })
                .Build();

            var mainWindow = _host.Services.GetService<MainWindow>();
            mainWindow?.Show();

            base.OnStartup(e);
        }

        protected override void OnExit(ExitEventArgs e)
        {
            _host?.Dispose();
            base.OnExit(e);
        }
    }
}
```

```csharp
// Models/IAppModel.cs - Business logic interface
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DesktopApp.Models
{
    public class Entity
    {
        public int Id { get; set; }
        public string Name { get; set; } = string.Empty;
        public DateTime CreatedAt { get; set; }
    }

    public interface IAppModel
    {
        event EventHandler<ModelChangedEventArgs> ModelChanged;
        
        Task<IEnumerable<Entity>> GetEntitiesAsync();
        Task<bool> AddEntityAsync(Entity entity);
        Task<bool> DeleteEntityAsync(int entityId);
        Task<bool> UpdateEntityAsync(Entity entity);
    }

    public class ModelChangedEventArgs : EventArgs
    {
        public string EventType { get; set; } = string.Empty;
        public object? Data { get; set; }
    }
}
```

```csharp
// ViewModels/MainViewModel.cs - MVVM ViewModel
using System;
using System.Collections.ObjectModel;
using System.ComponentModel;
using System.Runtime.CompilerServices;
using System.Threading.Tasks;
using System.Windows.Input;
using DesktopApp.Models;
using Microsoft.Extensions.Logging;

namespace DesktopApp.ViewModels
{
    public class MainViewModel : INotifyPropertyChanged
    {
        private readonly IAppModel _model;
        private readonly ILogger<MainViewModel> _logger;
        private string _newEntityName = string.Empty;
        private Entity? _selectedEntity;
        private bool _isLoading;

        public MainViewModel(IAppModel model, ILogger<MainViewModel> logger)
        {
            _model = model;
            _logger = logger;
            
            Entities = new ObservableCollection<Entity>();
            AddEntityCommand = new RelayCommand(async () => await AddEntityAsync(), CanAddEntity);
            DeleteEntityCommand = new RelayCommand(async () => await DeleteEntityAsync(), CanDeleteEntity);
            RefreshCommand = new RelayCommand(async () => await LoadEntitiesAsync());
            
            _model.ModelChanged += OnModelChanged;
            _ = LoadEntitiesAsync();
        }

        public ObservableCollection<Entity> Entities { get; }
        
        public string NewEntityName
        {
            get => _newEntityName;
            set
            {
                if (SetProperty(ref _newEntityName, value))
                {
                    AddEntityCommand.RaiseCanExecuteChanged();
                }
            }
        }
        
        public Entity? SelectedEntity
        {
            get => _selectedEntity;
            set
            {
                if (SetProperty(ref _selectedEntity, value))
                {
                    DeleteEntityCommand.RaiseCanExecuteChanged();
                }
            }
        }
        
        public bool IsLoading
        {
            get => _isLoading;
            set => SetProperty(ref _isLoading, value);
        }

        public RelayCommand AddEntityCommand { get; }
        public RelayCommand DeleteEntityCommand { get; }
        public RelayCommand RefreshCommand { get; }

        private async Task LoadEntitiesAsync()
        {
            try
            {
                IsLoading = true;
                var entities = await _model.GetEntitiesAsync();
                
                Entities.Clear();
                foreach (var entity in entities)
                {
                    Entities.Add(entity);
                }
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error loading entities");
            }
            finally
            {
                IsLoading = false;
            }
        }

        private async Task AddEntityAsync()
        {
            if (string.IsNullOrWhiteSpace(NewEntityName))
                return;

            try
            {
                var entity = new Entity { Name = NewEntityName.Trim() };
                if (await _model.AddEntityAsync(entity))
                {
                    NewEntityName = string.Empty;
                }
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error adding entity");
            }
        }

        private async Task DeleteEntityAsync()
        {
            if (SelectedEntity == null)
                return;

            try
            {
                await _model.DeleteEntityAsync(SelectedEntity.Id);
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error deleting entity");
            }
        }

        private bool CanAddEntity() => !string.IsNullOrWhiteSpace(NewEntityName);
        private bool CanDeleteEntity() => SelectedEntity != null;

        private void OnModelChanged(object? sender, ModelChangedEventArgs e)
        {
            if (e.EventType.Contains("entity"))
            {
                _ = LoadEntitiesAsync();
            }
        }

        public event PropertyChangedEventHandler? PropertyChanged;

        protected virtual void OnPropertyChanged([CallerMemberName] string? propertyName = null)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        protected bool SetProperty<T>(ref T field, T value, [CallerMemberName] string? propertyName = null)
        {
            if (EqualityComparer<T>.Default.Equals(field, value))
                return false;

            field = value;
            OnPropertyChanged(propertyName);
            return true;
        }
    }
}
```

### Java/Swing MVC Architecture

**Use when copilot.instructions.md specifies: Java, Swing, desktop**

```java
// src/main/java/com/company/DesktopApp.java - Application entry point
package com.company;

import com.company.controllers.MainController;
import com.company.models.AppModel;
import com.company.views.MainView;
import javax.swing.SwingUtilities;
import javax.swing.UIManager;

public class DesktopApp {
    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            try {
                // Set system look and feel
                UIManager.setLookAndFeel(UIManager.getSystemLookAndFeel());
                
                // Initialize Model-View-Controller architecture
                AppModel model = new AppModel();
                MainController controller = new MainController(model);
                MainView view = new MainView(controller);
                
                view.setVisible(true);
            } catch (Exception e) {
                e.printStackTrace();
            }
        });
    }
}
```

```java
// src/main/java/com/company/models/AppModel.java - Data and business logic layer
package com.company.models;

import java.sql.*;
import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.List;
import java.util.logging.Logger;

public class AppModel {
    private static final Logger LOGGER = Logger.getLogger(AppModel.class.getName());
    private final String dbPath;
    private final List<ModelObserver> observers;
    
    public interface ModelObserver {
        void modelChanged(String eventType, Object data);
    }
    
    public static class Entity {
        private int id;
        private String name;
        private LocalDateTime createdAt;
        
        public Entity() {}
        
        public Entity(String name) {
            this.name = name;
        }
        
        // Getters and setters
        public int getId() { return id; }
        public void setId(int id) { this.id = id; }
        public String getName() { return name; }
        public void setName(String name) { this.name = name; }
        public LocalDateTime getCreatedAt() { return createdAt; }
        public void setCreatedAt(LocalDateTime createdAt) { this.createdAt = createdAt; }
    }
    
    public AppModel() {
        this("app_data.db");
    }
    
    public AppModel(String dbPath) {
        this.dbPath = dbPath;
        this.observers = new ArrayList<>();
        initDatabase();
    }
    
    private void initDatabase() {
        String sql = """
            CREATE TABLE IF NOT EXISTS entities (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT NOT NULL,
                created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
            )
        """;
        
        try (Connection conn = DriverManager.getConnection("jdbc:sqlite:" + dbPath);
             Statement stmt = conn.createStatement()) {
            
            stmt.execute(sql);
            LOGGER.info("Database initialized successfully");
            
        } catch (SQLException e) {
            LOGGER.severe("Database initialization failed: " + e.getMessage());
        }
    }
    
    public void addObserver(ModelObserver observer) {
        observers.add(observer);
    }
    
    public void removeObserver(ModelObserver observer) {
        observers.remove(observer);
    }
    
    private void notifyObservers(String eventType, Object data) {
        for (ModelObserver observer : observers) {
            observer.modelChanged(eventType, data);
        }
    }
    
    public List<Entity> getEntities() {
        List<Entity> entities = new ArrayList<>();
        String sql = "SELECT id, name, created_at FROM entities ORDER BY created_at DESC";
        
        try (Connection conn = DriverManager.getConnection("jdbc:sqlite:" + dbPath);
             PreparedStatement pstmt = conn.prepareStatement(sql);
             ResultSet rs = pstmt.executeQuery()) {
            
            while (rs.next()) {
                Entity entity = new Entity();
                entity.setId(rs.getInt("id"));
                entity.setName(rs.getString("name"));
                entity.setCreatedAt(rs.getTimestamp("created_at").toLocalDateTime());
                entities.add(entity);
            }
            
        } catch (SQLException e) {
            LOGGER.severe("Error retrieving entities: " + e.getMessage());
        }
        
        return entities;
    }
    
    public boolean addEntity(Entity entity) {
        String sql = "INSERT INTO entities (name) VALUES (?)";
        
        try (Connection conn = DriverManager.getConnection("jdbc:sqlite:" + dbPath);
             PreparedStatement pstmt = conn.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {
            
            pstmt.setString(1, entity.getName());
            int affectedRows = pstmt.executeUpdate();
            
            if (affectedRows > 0) {
                try (ResultSet generatedKeys = pstmt.getGeneratedKeys()) {
                    if (generatedKeys.next()) {
                        entity.setId(generatedKeys.getInt(1));
                    }
                }
                notifyObservers("entity_added", entity);
                return true;
            }
            
        } catch (SQLException e) {
            LOGGER.severe("Error adding entity: " + e.getMessage());
        }
        
        return false;
    }
    
    public boolean deleteEntity(int entityId) {
        String sql = "DELETE FROM entities WHERE id = ?";
        
        try (Connection conn = DriverManager.getConnection("jdbc:sqlite:" + dbPath);
             PreparedStatement pstmt = conn.prepareStatement(sql)) {
            
            pstmt.setInt(1, entityId);
            int affectedRows = pstmt.executeUpdate();
            
            if (affectedRows > 0) {
                notifyObservers("entity_deleted", entityId);
                return true;
            }
            
        } catch (SQLException e) {
            LOGGER.severe("Error deleting entity: " + e.getMessage());
        }
        
        return false;
    }
}
```

### Electron/Node.js Architecture

**Use when copilot.instructions.md specifies: JavaScript/TypeScript, Electron, desktop**

```javascript
// main.js - Main process entry point
const { app, BrowserWindow, ipcMain } = require('electron');
const path = require('path');
const { AppModel } = require('./src/models/AppModel');
const { MainController } = require('./src/controllers/MainController');

class DesktopApp {
    constructor() {
        this.mainWindow = null;
        this.model = new AppModel();
        this.controller = new MainController(this.model);
        
        this.setupIPC();
    }
    
    createWindow() {
        this.mainWindow = new BrowserWindow({
            width: 1200,
            height: 800,
            webPreferences: {
                nodeIntegration: false,
                contextIsolation: true,
                preload: path.join(__dirname, 'preload.js')
            }
        });
        
        this.mainWindow.loadFile('src/views/index.html');
        
        if (process.env.NODE_ENV === 'development') {
            this.mainWindow.webContents.openDevTools();
        }
    }
    
    setupIPC() {
        // Handle entity operations
        ipcMain.handle('get-entities', async () => {
            return await this.controller.handleGetEntities();
        });
        
        ipcMain.handle('add-entity', async (event, entityData) => {
            return await this.controller.handleAddEntity(entityData);
        });
        
        ipcMain.handle('delete-entity', async (event, entityId) => {
            return await this.controller.handleDeleteEntity(entityId);
        });
        
        // Model change notifications
        this.model.addObserver((eventType, data) => {
            if (this.mainWindow) {
                this.mainWindow.webContents.send('model-changed', { eventType, data });
            }
        });
    }
}

const desktopApp = new DesktopApp();

app.whenReady().then(() => {
    desktopApp.createWindow();
    
    app.on('activate', () => {
        if (BrowserWindow.getAllWindows().length === 0) {
            desktopApp.createWindow();
        }
    });
});

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit();
    }
});
```

```javascript
// src/models/AppModel.js - Data and business logic layer
const sqlite3 = require('sqlite3').verbose();
const path = require('path');

class AppModel {
    constructor(dbPath = 'app_data.db') {
        this.dbPath = dbPath;
        this.observers = [];
        this.db = null;
        this.initDatabase();
    }
    
    initDatabase() {
        return new Promise((resolve, reject) => {
            this.db = new sqlite3.Database(this.dbPath, (err) => {
                if (err) {
                    console.error('Database connection error:', err);
                    reject(err);
                    return;
                }
                
                const sql = `
                    CREATE TABLE IF NOT EXISTS entities (
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        name TEXT NOT NULL,
                        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
                    )
                `;
                
                this.db.run(sql, (err) => {
                    if (err) {
                        console.error('Database initialization error:', err);
                        reject(err);
                    } else {
                        console.log('Database initialized successfully');
                        resolve();
                    }
                });
            });
        });
    }
    
    addObserver(observer) {
        this.observers.push(observer);
    }
    
    removeObserver(observer) {
        const index = this.observers.indexOf(observer);
        if (index > -1) {
            this.observers.splice(index, 1);
        }
    }
    
    notifyObservers(eventType, data) {
        this.observers.forEach(observer => {
            observer(eventType, data);
        });
    }
    
    async getEntities() {
        return new Promise((resolve, reject) => {
            const sql = 'SELECT id, name, created_at FROM entities ORDER BY created_at DESC';
            
            this.db.all(sql, [], (err, rows) => {
                if (err) {
                    console.error('Error retrieving entities:', err);
                    reject(err);
                } else {
                    resolve(rows);
                }
            });
        });
    }
    
    async addEntity(entity) {
        return new Promise((resolve, reject) => {
            const sql = 'INSERT INTO entities (name) VALUES (?)';
            
            this.db.run(sql, [entity.name], function(err) {
                if (err) {
                    console.error('Error adding entity:', err);
                    reject(err);
                } else {
                    const newEntity = {
                        id: this.lastID,
                        name: entity.name,
                        created_at: new Date().toISOString()
                    };
                    
                    // Notify observers
                    this.notifyObservers('entity_added', newEntity);
                    resolve(newEntity);
                }
            }.bind(this));
        });
    }
    
    async deleteEntity(entityId) {
        return new Promise((resolve, reject) => {
            const sql = 'DELETE FROM entities WHERE id = ?';
            
            this.db.run(sql, [entityId], function(err) {
                if (err) {
                    console.error('Error deleting entity:', err);
                    reject(err);
                } else if (this.changes > 0) {
                    // Notify observers
                    this.notifyObservers('entity_deleted', { id: entityId });
                    resolve(true);
                } else {
                    resolve(false);
                }
            }.bind(this));
        });
    }
}

module.exports = { AppModel };
```

```html
<!-- src/views/index.html - Renderer process UI -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desktop Application</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <header>
            <h1>Desktop Application</h1>
        </header>
        
        <main>
            <section class="input-section">
                <div class="form-group">
                    <label for="entity-name">Name:</label>
                    <input type="text" id="entity-name" placeholder="Enter entity name">
                    <button id="add-btn">Add Entity</button>
                </div>
            </section>
            
            <section class="list-section">
                <div class="list-header">
                    <h2>Entities</h2>
                    <button id="refresh-btn">Refresh</button>
                </div>
                
                <div id="entities-list" class="entities-list">
                    <!-- Entities will be populated here -->
                </div>
            </section>
        </main>
        
        <footer>
            <div id="status-bar" class="status-bar">Ready</div>
        </footer>
    </div>
    
    <script src="renderer.js"></script>
</body>
</html>
```

```javascript
// src/views/renderer.js - Renderer process logic
class MainView {
    constructor() {
        this.entities = [];
        this.setupEventListeners();
        this.loadEntities();
        
        // Listen for model changes from main process
        window.electronAPI.onModelChanged((event, data) => {
            this.handleModelChanged(data.eventType, data.data);
        });
    }
    
    setupEventListeners() {
        const addBtn = document.getElementById('add-btn');
        const entityNameInput = document.getElementById('entity-name');
        const refreshBtn = document.getElementById('refresh-btn');
        
        addBtn.addEventListener('click', () => this.addEntity());
        entityNameInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                this.addEntity();
            }
        });
        refreshBtn.addEventListener('click', () => this.loadEntities());
    }
    
    async loadEntities() {
        try {
            this.setStatus('Loading entities...');
            this.entities = await window.electronAPI.getEntities();
            this.renderEntities();
            this.setStatus('Ready');
        } catch (error) {
            console.error('Error loading entities:', error);
            this.setStatus('Error loading entities');
        }
    }
    
    async addEntity() {
        const nameInput = document.getElementById('entity-name');
        const name = nameInput.value.trim();
        
        if (!name) {
            this.showError('Name is required');
            return;
        }
        
        if (name.length < 2) {
            this.showError('Name must be at least 2 characters');
            return;
        }
        
        try {
            this.setStatus('Adding entity...');
            const newEntity = await window.electronAPI.addEntity({ name });
            nameInput.value = '';
            this.setStatus('Entity added successfully');
        } catch (error) {
            console.error('Error adding entity:', error);
            this.showError('Failed to add entity');
        }
    }
    
    async deleteEntity(entityId) {
        if (!confirm('Are you sure you want to delete this entity?')) {
            return;
        }
        
        try {
            this.setStatus('Deleting entity...');
            await window.electronAPI.deleteEntity(entityId);
            this.setStatus('Entity deleted successfully');
        } catch (error) {
            console.error('Error deleting entity:', error);
            this.showError('Failed to delete entity');
        }
    }
    
    renderEntities() {
        const listContainer = document.getElementById('entities-list');
        
        if (this.entities.length === 0) {
            listContainer.innerHTML = '<div class="empty-message">No entities found</div>';
            return;
        }
        
        const entitiesHTML = this.entities.map(entity => `
            <div class="entity-item" data-id="${entity.id}">
                <div class="entity-info">
                    <div class="entity-name">${this.escapeHtml(entity.name)}</div>
                    <div class="entity-date">${new Date(entity.created_at).toLocaleString()}</div>
                </div>
                <div class="entity-actions">
                    <button class="delete-btn" onclick="mainView.deleteEntity(${entity.id})">Delete</button>
                </div>
            </div>
        `).join('');
        
        listContainer.innerHTML = entitiesHTML;
    }
    
    handleModelChanged(eventType, data) {
        if (eventType.includes('entity')) {
            this.loadEntities();
        }
    }
    
    setStatus(message) {
        document.getElementById('status-bar').textContent = message;
    }
    
    showError(message) {
        this.setStatus(`Error: ${message}`);
        // Could also show a modal or toast notification
    }
    
    escapeHtml(text) {
        const div = document.createElement('div');
        div.textContent = text;
        return div.innerHTML;
    }
}

// Initialize the view when DOM is loaded
const mainView = new MainView();
```

## Quality Gates

### ✅ Architecture Compliance
- [ ] Architecture pattern matches copilot.instructions.md technology specification
- [ ] Proper separation of concerns implemented
- [ ] Observer/MVVM pattern correctly applied
- [ ] Dependency injection configured appropriately

### ✅ Code Quality
- [ ] Clean code principles followed
- [ ] Error handling implemented
- [ ] Logging appropriately configured
- [ ] Input validation present

### ✅ Maintainability
- [ ] Modular design with clear interfaces
- [ ] Testable architecture
- [ ] Documentation included
- [ ] Configuration externalized

## Implementation Strategy

### 1. Technology Detection

Analyze copilot.instructions.md configuration to determine:
- **Desktop framework** from primary_language and frontend technology fields
- **Platform requirements** for cross-platform vs. native development
- **Database requirements** for local data storage patterns
- **UI complexity** for appropriate architectural pattern selection

### 2. Architecture Pattern Selection

Select patterns based on detected technology and scale:
- **Python/wxPython**: MVC with observer pattern for loose coupling
- **C++/wxWidgets**: MVC with RAII and smart pointers for memory management
- **.NET/WPF**: MVVM with dependency injection and data binding
- **Java/Swing**: MVC with event-driven architecture and Swing components
- **Electron/Node.js**: MVC with IPC communication between main and renderer processes

### 3. Implementation Approach

Apply technology-specific desktop patterns:
- **Separation of concerns**: Clear Model-View-Controller or MVVM boundaries
- **Data management**: Local database integration with appropriate ORM/data access
- **Event handling**: Observer pattern or framework-specific event systems
- **UI responsiveness**: Asynchronous operations and proper threading
- **Error handling**: Comprehensive exception handling with user feedback

### 4. Success Criteria

Desktop architecture validation checklist:
- **Technology alignment**: Implementation follows framework best practices and conventions
- **User experience**: Responsive UI with proper event handling and validation
- **Data integrity**: Reliable local data storage with proper transaction handling
- **Maintainability**: Clear separation of concerns with testable architecture
- **Cross-platform**: Consistent behavior across target platforms

## Transition to Specialized Chatmodes

After completing desktop application architecture design:

- **For UI Implementation**: Switch to **@frontend-engineer** chatmode to implement detailed user interface components and styling
- **For Data Layer**: Switch to **@data-engineer** chatmode to optimize local database design and data access patterns
- **For Application Testing**: Switch to **@qa-engineer** chatmode to implement comprehensive testing strategies for desktop applications

**This prompt ensures desktop applications are architectured using patterns appropriate for the technology stack specified in copilot.instructions.md, maintaining consistency and best practices across different desktop frameworks.**