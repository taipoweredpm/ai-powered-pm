# 🚀 Generate My MCP Server

**Hey Copilot!** Please read this file and generate a complete MCP (Model Context Protocol) server based on the specifications below. Create all the necessary files, folders, and code to make this work.

## Server Configuration
- **Name**: my-first-mcp-server
- **Description**: A beginner-friendly MCP server with essential tools
- **Version**: 1.0.0
- **Language**: TypeScript
- **Target**: VS Code integration via MCP extension

## ✅ Tested & Working
This configuration has been successfully tested and all tools are fully functional!

## Tools

### calculator
**Description**: Performs basic mathematical operations

**Parameters**:
- `operation` (string, required): The math operation (add, subtract, multiply, divide, power, sqrt)
- `a` (number, required): First number
- `b` (number, optional): Second number (not needed for sqrt)

**Examples**:
```
calculator(operation="add", a=5, b=3) → 8
calculator(operation="sqrt", a=16) → 4
calculator(operation="power", a=2, b=3) → 8
```

### file_explorer
**Description**: Explores the file system safely

**Parameters**:
- `action` (string, required): Action to perform (list, info, read)
- `path` (string, required): File or directory path
- `max_files` (number, optional): Maximum files to list (default: 20)

**Examples**:
```
file_explorer(action="list", path="./src") → Lists files in src directory
file_explorer(action="info", path="./package.json") → File information
```

### random_generator
**Description**: Generates random data

**Parameters**:
- `type` (string, required): Type of random data (number, string, uuid, boolean)
- `min` (number, optional): Minimum value for numbers (default: 0)
- `max` (number, optional): Maximum value for numbers (default: 100)
- `length` (number, optional): Length for strings (default: 10)
- `count` (number, optional): Number of items to generate (default: 1)

**Examples**:
```
random_generator(type="number", min=1, max=10) → 7
random_generator(type="string", length=8) → "x7k9m2n1"
random_generator(type="uuid") → "f47ac10b-58cc-4372-a567-0e02b2c3d479"
```

### system_info
**Description**: Provides system and environment information

**Parameters**:
- `info_type` (string, required): Type of info (time, date, platform, memory, env, cpu)
- `format` (string, optional): Format for time/date (iso, local, timestamp)

**Examples**:
```
system_info(info_type="time", format="iso") → "2025-08-23T15:30:00Z"
system_info(info_type="platform") → "win32"
system_info(info_type="memory") → Memory usage statistics
system_info(info_type="cpu") → Detailed CPU information with model, cores, speed
```

---

**Ready to generate?** Ask Copilot: "Read this file and generate my MCP server!"

## � MOST IMPORTANT: VS Code Command Palette Setup

### 🎯 THE CRITICAL STEP - DO NOT SKIP THIS!

**This is the #1 most important step for VS Code integration. Everything depends on this:**

### Required VS Code Extensions
Install this extension in VS Code:
1. **Copilot MCP** - Core MCP support for integrating MCP servers with GitHub Copilot

### 🔥 COMMAND PALETTE METHOD (ESSENTIAL) 

**This is the ONLY method you should use - it's the most reliable and easiest:**

#### Step 1: Build Your Server
```bash
cd C:\Repos\First-MCP\demo\mcp-server
npm install
npm run build
```

#### Step 2: THE COMMAND PALETTE MAGIC ✨
**This is where the magic happens - pay close attention:**

1. **Open VS Code Command Palette**: `Ctrl+Shift+P`

2. **Type "MCP"** - you'll see MCP-related commands appear

3. **Select "MCP: Add Server"** (this is the key!)

4. **Choose "Command (stdio)"** when prompted for server type

5. **Enter the EXACT command**:
   ```
   node C:\Repos\First-MCP\demo\mcp-server\dist\index.js
   ```

6. **Test immediately in Copilot Chat** (`Ctrl+Alt+I`):
   ```
   calculate 25*7
   ```
   If you get "Result: 175", it's working perfectly!

#### Why This Method is Essential:
- ✅ **VS Code handles most configuration automatically**
- ✅ **Built-in validation and error checking** 
- ✅ **Immediately available after adding**
- ✅ **Most reliable integration method**
- ✅ **Works with existing mcp.json or creates new entries**

### 🔧 What You Still Need: The mcp.json File

**Important**: You still need to ensure the `mcp.json` file exists with proper configuration. The Command Palette method works best when this file is already set up correctly.

**The Command Palette method will:**
- ✅ Add your server to the existing mcp.json configuration
- ✅ Validate the server configuration
- ✅ Make the server immediately available to Copilot

**But you still need to ensure mcp.json exists. The generated server will automatically create this file with:**
```json
{
  "servers": {
    "my-first-mcp-server": {
      "type": "stdio", 
      "command": "node",
      "args": [
        "C:\\Repos\\First-MCP\\demo\\mcp-server\\dist\\index.js"
      ]
    }
  }
}
```

### ⚠️ CRITICAL: Project Structure Requirements

Your `package.json` MUST include a `bin` field for VS Code integration:
```json
{
  "name": "my-first-mcp-server",
  "bin": {
    "my-first-mcp-server": "dist/index.js"
  }
}
```

### 🎯 Alternative: Manual Configuration (You'll Still Need This!)

**Important**: Even if you use the Command Palette method, you may need to ensure the mcp.json file exists first. Here's how to create it:

Create the VS Code user settings file: `%APPDATA%\Code\User\mcp.json`:
```json
{
  "servers": {
    "my-first-mcp-server": {
      "type": "stdio",
      "command": "node", 
      "args": [
        "C:\\Repos\\First-MCP\\demo\\mcp-server\\dist\\index.js"
      ]
    }
  }
}
```

**Recommended Approach:**
1. **First**: Create the mcp.json file with the configuration above
2. **Then**: Use the Command Palette method to verify and activate the server
3. **Finally**: Test with `calculate 25*7` in Copilot Chat

**⚠️ KEY SUCCESS FACTORS:**
- 🔥 **USE THE COMMAND PALETTE METHOD** - This is the #1 most important step!
- ✅ **Follow the exact steps above** - Don't skip the Command Palette process
- ✅ **Use absolute paths** - Always use full paths to the compiled `dist/index.js`
- ✅ **Test the command first** - Verify with: `node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"`
- ✅ **Test immediately** - Try `calculate 25*7` in Copilot Chat right after adding

**⚠️ Common Configuration Mistakes to Avoid:**
- ❌ Don't use old `mcpServers` format (use `servers` instead)
- ❌ Don't use `["path"]` (extra brackets around path)
- ❌ Don't try npm package references for local development
- ❌ Don't use relative paths
- ✅ Use absolute paths with double backslashes on Windows
- ✅ Use `"type": "stdio"` for local command execution
- ✅ Test the exact command in terminal first

#### 3. Build Process (Execute in mcp-server directory)
```bash
# Navigate to the mcp-server directory FIRST
cd mcp-server
npm install
npm run build

# Quick test (optional) - server will run and appear to hang (this is normal)
# Press Ctrl+C to stop after you see the success message
npm start
```

**🚨 Server Behavior Note**: When you run `npm start`, the server will show `[MCP Server] My First MCP Server started successfully` and then appear to "hang" - this is completely normal! MCP servers run continuously and wait for stdio communication from VS Code. Use `Ctrl+C` to stop the server when testing manually.

#### 4. Testing the Server
After building, test the server directly:
```bash
# IMPORTANT: Must be run from mcp-server directory OR with full path
cd mcp-server
npm start
# OR directly with node:
node dist/index.js

# OR with absolute path (works from any directory):
node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"
```
You should see: `[MCP Server] My First MCP Server started successfully`

**⚠️ IMPORTANT**: The server will appear to "hang" after showing the success message - this is NORMAL! The MCP server runs continuously and waits for stdio input/output from VS Code. To stop the server for testing purposes, use `Ctrl+C` in the terminal.

#### 5. 🔥 THE MOMENT OF TRUTH: Command Palette Integration

**This is the most critical step - everything depends on this working correctly:**

1. **Open Command Palette**: `Ctrl+Shift+P`

2. **Type "MCP"** and select **"MCP: Add Server"**

3. **Choose "Command (stdio)"**

4. **Enter**: `node C:\Repos\First-MCP\demo\mcp-server\dist\index.js`

5. **Immediately test in Copilot Chat** (`Ctrl+Alt+I`):
   ```
   calculate 25*7
   ```
   **Expected result**: Result: 175

**If this doesn't work, check the troubleshooting section below!**

**✅ Success Indicators:**
- ✅ Server shows startup message and "hangs" (normal behavior)
- ✅ VS Code MCP commands appear in Command Palette
- ✅ Copilot Chat gives actual calculation results, not just text explanations
- ✅ All 4 tools (calculator, file_explorer, random_generator, system_info) work with real data
- ✅ CPU information shows actual processor model and specifications

## 📋 Generation Instructions for Copilot

When I ask you to generate this MCP server, please:

### 1. Create Project Structure
```
mcp-server/
├── package.json          # Node.js project with MCP SDK + BIN field
├── tsconfig.json         # TypeScript configuration  
├── src/
│   ├── index.ts         # Main MCP server entry point
│   └── tools/           # Individual tool implementations
│       ├── calculator.ts
│       ├── file-explorer.ts
│       ├── random-generator.ts
│       └── system-info.ts
└── dist/                # Build output (created by tsc)
    └── index.js        # Compiled server entry
```

### 2. Required Dependencies
- `@modelcontextprotocol/sdk` - Core MCP SDK
- `typescript` and `@types/node` - TypeScript support
- `uuid` and `@types/uuid` - For UUID generation tool
- Any other dependencies needed for the tools

### 3. Implementation Requirements
- **Proper error handling** - Validate all inputs, return descriptive error messages
- **Type safety** - Full TypeScript types for all parameters and responses
- **Security** - Safe file operations, input sanitization, no shell execution
- **MCP compliance** - Follow the Model Context Protocol specification exactly
- **ES Modules** - Use import/export syntax (not require)
- **Stdio Transport** - Use stdio for VS Code communication

### 4. Critical Build Configuration

#### package.json Requirements:
```json
{
  "type": "module",
  "bin": {
    "my-first-mcp-server": "dist/index.js"
  },
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js"
  }
}
```

#### tsconfig.json Requirements:
```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "ESNext",
    "moduleResolution": "Node",
    "outDir": "./dist"
  }
}
```

### 5. Working Directory Guidelines
- **ALWAYS** execute build commands from the `mcp-server` directory
- **ALWAYS** run `npm start` from the `mcp-server` directory (not parent directory)
- **NEVER** try to build from parent directories
- Use `cd mcp-server` before running `npm install`, `npm run build`, or `npm start`
- Test the compiled server with: `node dist/index.js` (from mcp-server directory)

### 6. Each Tool Should Include
- Input parameter validation with detailed error messages
- Comprehensive error handling for edge cases
- Clear success/error responses with proper formatting
- TypeScript interfaces for all parameters
- JSDoc comments for documentation
- Proper ES module imports (no require statements)

### 7. VS Code Integration Steps
1. Build the project: `npm run build` (from mcp-server directory)
2. Add server to VS Code mcp.json with absolute path to dist/index.js
3. Restart VS Code completely
4. Test tools via Copilot Chat with specific commands

### 8. After Generation - Complete Setup Process
- **Step 1**: Generate the server and build it successfully
- **Step 2**: Create the mcp.json configuration file (the generation process will do this automatically)
- **Step 3**: Use the Command Palette method (`Ctrl+Shift+P` → "MCP: Add Server") to activate and verify
- **Step 4**: Test immediately with `calculate 25*7` in Copilot Chat
- **Make both methods clear**: Explain that mcp.json needs to exist AND Command Palette is the best way to activate it
- Provide clear setup instructions with correct directory navigation
- Show exact build commands with proper working directory
- **Important**: Explain that MCP servers run continuously and will appear to "hang" after starting (this is normal behavior)
- Include example usage commands for each tool
- Include troubleshooting section for common issues

**Make it production-ready but beginner-friendly!** 🎯

## 🧪 Testing Your MCP Server - Simple Prompts That Work!

Once your MCP server is running and configured in VS Code, you can test it using natural language in **Copilot Chat**. Here are proven prompts that work:

### 🧮 Calculator Tool Examples
**Simple Math Prompts:**
- `calculate 25*7` → Result: 175
- `what's 25 * 8?` → Result: 200
- `Calculate the square root of 144` → Result: 12
- `What's 2 to the power of 10?` → Result: 1024
- `Add 156 and 789` → Result: 945
- `Divide 500 by 25` → Result: 20

### 🎲 Random Generator Tool Examples
**Natural Random Data Requests:**
- `generate some random data` → Multiple types of random data
- `Generate 5 random numbers between 1 and 100` → [53, 14, 51, etc.]
- `Create a random string with 8 characters` → "AaWuZTZ6"
- `Generate a UUID` → "adbf3b85-1665-4ee7-a051-e0a238310ff9"
- `Give me 4 random boolean values` → [true, false, false, false]
- `Generate 3 random strings each 12 characters long` → ["QiBq9qR5BA4Z", etc.]

### 📁 File Explorer Tool Examples
**File System Exploration:**
- `List files in my project directory` → Shows project structure
- `Show me what's in the src folder` → Lists source files
- `Get information about package.json` → File details and metadata
- `List all TypeScript files in the tools directory` → Shows .ts files
- `Show files in C:\Repos\First-MCP\demo` → Directory contents

### 💻 System Info Tool Examples
**System Information Requests:**
- `What's the current time?` → ISO timestamp
- `Show me memory usage` → RAM usage statistics
- `What platform am I running on?` → Windows system info
- `Display system information` → Complete system details
- `Show environment variables` → System environment
- `What's today's date?` → Current date/time
- `Tell me about my CPU` → Detailed processor information with model, cores, speed

## 🎯 How to Test Your MCP Integration

### 🔥 Step 1: THE COMMAND PALETTE METHOD (ESSENTIAL!)

**This is the #1 most important step - everything depends on this:**

1. **Open VS Code Command Palette**: `Ctrl+Shift+P`
2. **Type "MCP"** and select **"MCP: Add Server"**
3. **Choose "Command (stdio)"**
4. **Enter the exact command**:
   ```
   node C:\Repos\First-MCP\demo\mcp-server\dist\index.js
   ```

### Step 2: Immediate Testing
**Right after adding via Command Palette, test these:**

**Quick Math Test:**
```
calculate 25*7
```

**Random Data Test:**
```
generate some random data
```

**File System Test:**
```
list files in my project directory
```

**System Info Test:**
```
what's the system information?
```

**CPU Information Test:**
```
tell me about my CPU
```

### Step 3: Verify Success
You'll know your Command Palette integration worked when:
- ✅ Copilot responds with actual calculations, not just text
- ✅ Random data shows real generated values with proper formatting
- ✅ File listings show your actual project files and directories
- ✅ System info shows real data about your Windows machine

**If any of these don't work, the Command Palette step didn't work correctly - try it again!**

## 🚀 Advanced Test Prompts

Once basic testing works, try these more complex examples:

**Complex Calculations:**
- `Calculate the square root of 144, then multiply by 5`
- `What's 2^10 divided by 4?`

**Specific Random Data:**
- `Generate 10 random numbers between 50 and 200`
- `Create 5 UUIDs for testing`
- `Generate a 16-character random password string`

**File System Deep Dive:**
- `Show me all the TypeScript files in my MCP server`
- `Get detailed info about my package.json file`
- `List everything in the tools directory`

**System Analysis:**
- `Show current memory usage and system specs`
- `What's my Node.js version and platform info?`
- `Display environment variables related to development`
- `Tell me about my processor and CPU details`
- `What CPU do I have and how old is my computer?`

## ✅ Verified Working Examples
These exact prompts have been tested and work perfectly:

**Calculator**: `calculate 25*7` → Result: 175
**Random Generator**: `generate some random data` → Numbers, strings, UUIDs, booleans
**File Explorer**: `list files in my project directory` → Complete project structure
**System Info**: `what's the system information?` → Complete system details and live data

## 🐛 Troubleshooting

### Common Issues

**"Missing script: start" error**: This happens when you try to run `npm start` from the wrong directory. Always run it from the `mcp-server` directory, not the parent directory:
```bash
# ❌ Wrong - from parent directory
cd c:\Repos\First-MCP\demo
npm start  # Error: Missing script: "start"

# ✅ Correct - from mcp-server directory  
cd c:\Repos\First-MCP\demo\mcp-server
npm start  # Works correctly

# ✅ Alternative - use absolute path (works from any directory)
node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"
```

**"Cannot find module" error**: This happens when Node.js can't resolve the ES modules due to incorrect working directory:
```bash
# ❌ This will fail if run from wrong directory
node dist/index.js

# ✅ Use full absolute path instead
node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"

# ✅ Or ensure you're in the correct directory first
cd c:\Repos\First-MCP\demo\mcp-server
node dist/index.js
```

**Build fails**: Make sure you're in the `mcp-server` directory when running `npm install` and `npm run build`.

**VS Code doesn't recognize server**: 
- Check the absolute path in `mcp.json`
- Restart VS Code completely
- Ensure the server builds without errors
- Test the server directly with `npm start` from the mcp-server directory
- Verify the `mcp.json` file exists: `Test-Path "$env:APPDATA\Code\User\mcp.json"`

**MCP configuration file missing**: 
**The mcp.json file is required! Here's how to create it:**

**Method 1 - Automatic (Recommended)**: The generation process should create this automatically

**Method 2 - Manual Creation**: Use this PowerShell command:
```powershell
New-Item -ItemType Directory -Force -Path "$env:APPDATA\Code\User"
@"
{
  "servers": {
    "my-first-mcp-server": {
      "type": "stdio",
      "command": "node",
      "args": [
        "C:\\Repos\\First-MCP\\demo\\mcp-server\\dist\\index.js"
      ]
    }
  }
}
"@ | Out-File -FilePath "$env:APPDATA\Code\User\mcp.json" -Encoding UTF8
```

**Method 3 - Command Palette**: After creating the file above, use `Ctrl+Shift+P` → "MCP: Add Server" to verify it's working

**Server fails to start in VS Code**: 
1. **First, test the command directly**: `node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"`
   - The server should show the success message and then "hang" (this is normal - keep it running)
2. If that works, the issue is in the MCP configuration
3. **🔥 USE THE COMMAND PALETTE METHOD** - This is the most reliable approach:
   - `Ctrl+Shift+P` → "MCP: Add Server" → "Command (stdio)" → Enter the node command
4. **Restart VS Code completely** after adding via Command Palette
5. Check VS Code's Output panel for detailed error messages

**Tools don't work in Copilot Chat**: 
- **🔥 Did you use the Command Palette method?** This is the #1 most common issue!
- Try the Command Palette steps again: `Ctrl+Shift+P` → "MCP: Add Server"
- Test with simple prompts first: `calculate 25*7`
- Check VS Code's Output panel for MCP-related errors
- Verify the Copilot MCP extension is installed and enabled

**Permission errors**: 
- Make sure the compiled `dist/index.js` has execute permissions
- Try running VS Code as administrator (Windows)

### Getting Help

**🔥 THE #1 TROUBLESHOOTING STEP: Did you use the Command Palette?**
- Most issues are solved by using: `Ctrl+Shift+P` → "MCP: Add Server"
- This is the most reliable method and should always be your first attempt

**If Command Palette method doesn't work:**
1. Verify VS Code extensions are installed and enabled (Copilot MCP extension)
2. Check VS Code's Output panel for detailed error messages
3. Restart VS Code completely after adding the server
4. Test the server command directly: `node "C:\Repos\First-MCP\demo\mcp-server\dist\index.js"`
5. Make sure the server builds successfully: `npm run build` from mcp-server directory
