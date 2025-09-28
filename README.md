# Nginx Deployment with Ansible Role

## 📖 Overview
This project demonstrates infrastructure automation using Ansible to deploy Nginx web servers with dynamic content. 

It showcases best practices including role-based organization, handler configuration, and containerized testing environments.

## 🎯 Purpose
The main objectives of this project are:
- **Learn Ansible Automation**: Master configuration management and deployment automation
- **Implement Role-Based Architecture**: Organize code into reusable, modular components
- **Master Nginx Configuration**: Web server deployment, port configuration, and dynamic content serving

## 🏗️ Project Architecture
Deploy_Nginx/

├── roles/nginx/     # Ansible Role

│ ├── tasks/main.yml       # Installation and configuration tasks

│ ├── handlers/main.yml   # Service management handlers

│ ├── templates/   # Jinja2 templates

│ │ ├── index.html.j2   # Dynamic HTML template

│ │ └── nginx.conf.j2   # Nginx configuration template

│ └── defaults/main.yml   # Configurable variables

├── inventory.yml   # Target hosts definition

├── playbook.yml   # Main deployment playbook

└── docker-compose.yml   # Test environment setup


## 🚀 Implementation Steps

### Phase 1: Environment Setup
1. **Create Docker test environment** with multiple containers
2. **Configure Ansible inventory** to target containers
3. **Test connectivity** between Ansible and targets

### Phase 2: Basic Playbook Development
1. **Write initial playbook** for Nginx installation
2. **Implement handlers** for service management
3. **Test basic functionality**

### Phase 3: Advanced Features
1. **Create dynamic HTML templates** with host-specific information
2. **Configure Nginx** to listen on custom port (8080)
3. **Implement configuration validation**

### Phase 4: Role Conversion
1. **Organize code into Ansible Role structure**
2. **Separate tasks, handlers, and templates**
3. **Make configuration configurable via variables**

### Phase 5: Testing & Validation
1. **Run comprehensive tests**
2. **Verify dynamic content generation**
3. **Ensure port configuration works**

## 🛠️ How We Implemented It

### 🔧 Key Components
1. **Ansible Role Structure**: Modular organization for reusability
2. **Handler Configuration**: Automatic service restart on configuration changes
3. **Jinja2 Templates**: Dynamic content generation with Ansible facts
4. **Docker Integration**: Containerized testing environment
5. **Port Configuration**: Nginx customized to run on port 8080

### 💡 Technical Highlights
- **Dynamic HTML**: Each server displays unique hostname and IP address
- **Service Management**: Proper handling of Nginx service states
- **Configuration Management**: Safe configuration updates with validation
- **Role Variables**: Configurable parameters for flexibility

## 🏃‍♂️ How to Run and Test

### Step 1: Clone and Setup

    git clone https://github.com/your-username/Nginx-deployment-with-Ansible-Role.git
    cd Nginx-deployment-with-Ansible-Role

### Step 2: Start Test Environment

    docker-compose up -d

### Step 3: Get Container IPs and Update Inventory

    docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' web-1
    docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' web-2
    
# Update inventory.yml with the obtained IPs
### Step 4: Run the Deployment

    ansible-playbook -i inventory.yml playbook.yml
    

<img width="1013" height="810" alt="image" src="https://github.com/user-attachments/assets/0d7b55a7-aed0-4abb-a0cc-0c855f4ba522" />


### Step 5: Verify Deployment

# Test web server accessibility

    ansible -i inventory.yml all -a "curl -s http://localhost:8080"
    

<img width="1100" height="470" alt="image" src="https://github.com/user-attachments/assets/e63ef206-32fe-4df3-a876-9889e61c2602" />


# Check service status

    ansible -i inventory.yml all -a "systemctl status nginx"


## 🎓 Learning Outcomes

Through this project, you'll master:

Ansible playbook and role development

Infrastructure as Code principles

Web server configuration and management

Containerized environment testing

DevOps automation best practices


    
