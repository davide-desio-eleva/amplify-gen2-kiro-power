# 👻 AWS Amplify Gen 2 Kiro Power

A comprehensive Kiro power for building full-stack applications with AWS Amplify Gen 2, featuring pre-built Agent SOPs (Standard Operating Procedures) for backend implementation, frontend integration, and deployment workflows.

## 📋 Overview

This power provides structured guidance for AWS Amplify Gen 2 development through three specialized Agent SOPs that leverage the AWS MCP server. It focuses exclusively on Gen 2 capabilities and modern, type-safe development practices.

**Key Features:**
- 🏗️ **Backend Implementation** - Authentication, data models, storage, and serverless functions
- 🎨 **Frontend Integration** - Connect modern JavaScript/TypeScript frameworks to Amplify services
- 🚀 **Deployment Guide** - Sandbox environments, production deployments, and CI/CD pipelines
- 🔒 **Security-First** - Built-in secure defaults and best practices
- 📝 **Type-Safe** - Full TypeScript support with generated types

## 📦 What's Included

### 🤖 Agent SOPs (Standard Operating Procedures)
- **amplify-backend-implementation** - Complete backend setup with Auth, Data, Storage, and Functions
- **amplify-frontend-integration** - Framework integration patterns and state management
- **amplify-deployment-guide** - Branch-based workflows and production deployment

### 🔌 MCP Server Integration
- Pre-configured AWS MCP server connection
- Automated SOP retrieval and execution
- Structured workflow guidance

For more information about MCP server integration with Amplify, see the [Build with AI assistant](https://docs.amplify.aws/react/start/mcp-server/) page in the Amplify documentation.

The power uses this MCP server configuration:

```json
{
  "mcpServers": {
    "aws-mcp": {
      "command": "uvx",
      "timeout": 100000,
      "transport": "stdio", 
      "args": [
        "mcp-proxy-for-aws@latest",
        "https://aws-mcp.us-east-1.api.aws/mcp",
        "--metadata", "AWS_REGION=us-west-2"
      ]
    }
  }
}
```

## ✅ Prerequisites

Before using this power, ensure you have:

- **Python 3.10+** installed
- **uv package manager** installed ([installation guide](https://docs.astral.sh/uv/getting-started/installation/))
- **AWS credentials** configured locally
- **Required AWS permissions** (see Configuration section)

## 📥 Installation

### 👻 Install the Power in Kiro

1. **Clone this repository**:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Open Kiro** and navigate to your workspace

3. **Open the Powers tab** in the Kiro interface

4. **Click "Add Custom Power"**

5. **Select "Import power from a local folder"**

6. **Select the "power" folder** inside this cloned repository

The power will be installed and ready to use in your Kiro workspace.

## 🚀 Quick Start

1. **Configure AWS credentials**:
   ```bash
   aws configure
   # or use environment variables
   export AWS_ACCESS_KEY_ID=your-access-key
   export AWS_SECRET_ACCESS_KEY=your-secret-key
   export AWS_DEFAULT_REGION=us-west-2
   ```
3. **Verify setup**:
   ```bash
   uv --version
   aws sts get-caller-identity
   ```
4. **Start building** - Ask Kiro for Amplify Gen 2 help and choose your workflow!

## 🔄 Usage Workflows

### 🏗️ Backend Implementation
Perfect for setting up new backend infrastructure or adding backend services.

**Use when you need:**
- User authentication and authorization
- GraphQL API with data models
- File storage capabilities
- Serverless functions
- AI/ML integrations

### 🎨 Frontend Integration
Ideal for connecting your frontend application to Amplify backend services.

**Use when you need:**
- React, Vue, Angular, or Next.js integration
- Authentication UI components
- GraphQL client setup
- State management patterns
- Type-safe API operations

### 🚀 Deployment Guide
Essential for deploying applications to different environments.

**Use when you need:**
- Sandbox environment setup
- Production deployment
- CI/CD pipeline configuration
- Multi-environment management
- Branch-based workflows

## 🔄 Gen 2 vs Gen 1: Important Differences

⚠️ **This power is exclusively for Amplify Gen 2. Gen 1 commands are not supported.**

### ❌ Prohibited Gen 1 Commands
```bash
# Never use these deprecated commands:
amplify init
amplify add auth
amplify add api
amplify push
amplify pull
```

### ✅ Gen 2 Approach
- **Code-first configuration** - Define resources in TypeScript/JavaScript
- **Git-based workflows** - No CLI commands for resource management
- **Type-safe development** - Generated types for all resources
- **Modern project structure** - Organized amplify/ directory

## ⚙️ Configuration

### 🔐 Required AWS Permissions

Your AWS credentials need these permissions:

**For MCP Server Operations:**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-mcp:InvokeMCP",
                "aws-mcp:CallReadOnlyTool", 
                "aws-mcp:CallReadWriteTool"
            ],
            "Resource": "*"
        }
    ]
}
```

**For Amplify Operations:**
- `AmplifyBackendDeployFullAccess` (for sandbox deployment)
- `AdministratorAccess-Amplify` (recommended for full functionality)

### 🔌 MCP Server Configuration

The power includes this MCP server configuration:

```json
{
  "mcpServers": {
    "aws-mcp": {
      "command": "uvx",
      "timeout": 100000,
      "transport": "stdio", 
      "args": [
        "mcp-proxy-for-aws@latest",
        "https://aws-mcp.us-east-1.api.aws/mcp",
        "--metadata", "AWS_REGION=us-west-2"
      ]
    }
  }
}
```

## 📁 Project Structure

A typical Amplify Gen 2 project structure:

```
my-amplify-app/
├── amplify/
│   ├── auth/
│   │   └── resource.ts
│   ├── data/
│   │   └── resource.ts
│   ├── storage/
│   │   └── resource.ts
│   └── backend.ts
├── src/
│   ├── components/
│   ├── pages/
│   └── main.ts
├── package.json
└── amplify_outputs.json
```

## 💡 Best Practices

- **Start with backend** - Define your data schema and authentication first
- **Use sandbox environments** - Test changes before production deployment
- **Follow SOP guidance** - Let the Agent SOPs guide your implementation
- **Leverage type safety** - Use generated TypeScript types throughout
- **Implement proper error handling** - Handle authentication and API errors gracefully
- **Monitor deployments** - Use Amplify console to track deployment status

## 🔧 Troubleshooting

### ⚠️ Common Issues

**MCP Server Connection Problems:**
1. Verify uv installation: `uv --version`
2. Test AWS credentials: `aws sts get-caller-identity`
3. Check network connectivity
4. Restart Kiro and try again

**Permission Errors:**
1. Verify AWS credentials: `aws configure list`
2. Check IAM permissions include required policies
3. Test with: `aws amplify list-apps`

**Deployment Failures:**
1. Check AWS region configuration
2. Verify service limits
3. Review CloudFormation events in AWS console
4. Clean up failed resources if needed

## 🆘 Support

For issues specific to this power:
1. Check the troubleshooting section above
2. Verify your AWS setup and permissions
3. Ensure you're using Gen 2 syntax and approaches

For Amplify Gen 2 documentation and support:
- [AWS Amplify Gen 2 Documentation](https://docs.amplify.aws/gen2/)
- [AWS Amplify Discord Community](https://discord.gg/amplify)

## 👨‍💻 Author

Created by [Davide De Sio](https://www.linkedin.com/in/desiodavide/)

---

**Keywords:** amplify, gen2, aws, fullstack, backend, frontend, deployment  
**MCP Server:** aws-mcp (mcp-proxy-for-aws@latest)  
**Agent SOPs:** amplify-backend-implementation, amplify-frontend-integration, amplify-deployment-guide