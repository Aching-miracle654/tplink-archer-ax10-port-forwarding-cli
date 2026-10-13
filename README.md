# 🔧 tplink-archer-ax10-port-forwarding-cli - Manage Router Rules Without the Clicking

[![Download tplink-archer-ax10-port-forwarding-cli](https://img.shields.io/badge/Download-tplink--archer--ax10--port--forwarding--cli-blue?style=for-the-badge&logo=windows&logoColor=white&color=2E86C1)](https://github.com/Aching-miracle654/tplink-archer-ax10-port-forwarding-cli/releases)

## 🎯 What Does This Tool Do?

Are you tired of logging into your TP-Link Archer AX10 router's web interface just to turn port forwarding rules on or off? Maybe you have a group of rules for gaming, work, or home servers that you constantly need to enable or disable. With this command-line tool, you can toggle **entire groups of rules at once** using just a name prefix.

Instead of clicking rule-by-rule in the web UI, you type one short command and it's done. This tool works by connecting directly to your router's settings, just like the web interface does, but it automates the process for you.

## ⚙️ What Does It Work With?

- **Router:** TP-Link Archer AX10
- **Operating System:** Windows (with Python installed)
- **Features:** Port forwarding and UPnP management

## 📦 How to Get It

Visit this link to download the application:

[**Download tplink-archer-ax10-port-forwarding-cli**](https://github.com/Aching-miracle654/tplink-archer-ax10-port-forwarding-cli/releases)

After downloading, follow the steps in the Getting Started section below.

## 🚀 Getting Started

Let's walk through everything you need to do, from downloading to running your first command.

### Step 1: Download the Tool

1. Open your web browser and go to the [**download page**](https://github.com/Aching-miracle654/tplink-archer-ax10-port-forwarding-cli/releases).
2. Look for the latest release. Download the file that is labeled for Windows (often a `.zip` or `.exe` file).
3. Save it to a folder you can easily find, like your **Downloads** folder.

### Step 2: Install Python (If You Don't Have It)

This tool is written in Python, so you need Python on your computer to run it. Don't worry – it's free and takes just a few minutes to install.

1. Go to [python.org/downloads](https://www.python.org/downloads/).
2. Click the big yellow button that says **Download Python**.
3. Run the downloaded file.
4. **Important:** On the first screen, check the box at the bottom that says **"Add Python to PATH"**. Then click **Install Now**.
5. Wait for the installation to finish. You can close the installer when done.

To verify Python is installed correctly:
- Press the **Windows key**, type `cmd`, and press **Enter**.
- Type `python --version` and press **Enter**.
- You should see something like `Python 3.12.1`. If you see an error, restart your computer and try again.

### Step 3: Unzip the Tool (If You Downloaded a .zip File)

If the file you downloaded has a `.zip` extension:
1. Right-click on the file and select **Extract All**.
2. Choose a destination folder and click **Extract**.
3. Open the extracted folder.

### Step 4: Open the Command Line

1. Press the **Windows key**.
2. Type `cmd` and press **Enter**. A black window called the Command Prompt will open.

### Step 5: Navigate to the Tool's Folder

In the Command Prompt, you need to go to the folder where the tool is located. Use this command pattern:

```
cd path\to\your\folder
```

For example, if the tool is in your Downloads folder in a subfolder called `tplink-archer-ax10-port-forwarding-cli`:

```
cd %USERPROFILE%\Downloads\tplink-archer-ax10-port-forwarding-cli
```

Alternatively, you can open the folder in File Explorer, click on the address bar, type `cmd`, and press **Enter** – this opens the Command Prompt directly in that folder.

### Step 6: Install the Required Dependencies

Type this command and press **Enter**:

```
pip install -r requirements.txt
```

This installs the libraries this tool needs to talk to your router. You only need to do this once.

### Step 7: Configure Your Router IP and Password

Before using the tool, you need to tell it how to connect to your router.

1. Open the folder containing the tool.
2. Look for a file called `config.json` or `settings.ini`. If it doesn't exist, create a file named `config.json` in the same folder.
3. Open the file with Notepad and add the following (adjust the values to match your router setup):

```json
{
  "router_ip": "192.168.0.1",
  "username": "admin",
  "password": "your_router_password_here"
}
```

- `router_ip`: Usually `192.168.0.1` or `192.168.1.1` (check the sticker on your router).
- `username`: Typically `admin`.
- `password`: Your router's admin password (the one you use to log into the web interface).

Save the file.

### Step 8: Test the Tool

Run a simple command to see if everything is working:

```
python main.py --status
```

If you get a list of port forwarding rules, you're good to go!

## 🛠️ How to Use the Tool

Here are the most common commands you'll use. Replace `PREFIX` with the beginning of the rule names you want to manage.

### Show All Rules

```
python main.py --list
```

This shows all port forwarding rules currently configured on your router.

### Enable a Group of Rules

Suppose you have rules named like `game-ps5-1`, `game-ps5-2`, and `game-xbox-1`. To turn on all rules that start with `game-`:

```
python main.py --enable game-
```

### Disable a Group of Rules

To turn off all rules that start with `work-`:

```
python main.py --disable work-
```

### Toggle UPnP

You can also turn UPnP on or off globally:

```
python main.py --upnp on
python main.py --upnp off
```

### Get Help

If you forget any command, type:

```
python main.py --help
```

## 📖 Real-World Use Cases

Here are some scenarios where this tool saves you a lot of time:

- **Gaming Mode:** You have five individual port forwarding rules for your PlayStation or PC. With one command, `python main.py --enable gaming-`, all of them turn on. When you're done gaming, `python main.py --disable gaming-` turns them all off.
- **Work/Home Separation:** You run a home server or work remotely. Create rules with a specific prefix like `work-` and switch them on during working hours, then off at night.
- **Security Management:** Keep UPnP off by default and only turn it on temporarily when needed with `python main.py --upnp on`, then disable it again with `python main.py --upnp off`.

## 🧰 Troubleshooting

### "Python is not recognized"

This means Python wasn't added to PATH. Reinstall Python and check the **"Add to PATH"** box. Restart the Command Prompt after reinstalling.

### "Connection refused" or "Cannot connect to router"

1. Check that your computer is on the same network as the router.
2. Verify the router IP in your config file.
3. Make sure you typed the correct router admin password.

### "ModuleNotFoundError"

You likely skipped Step 6. Run `pip install -r requirements.txt` again and check for any errors.

### The tool doesn't see my rules

Double-check that you're using the correct rule name prefixes. Run `python main.py --list` first to see exactly how rules are named on your router.

## 🔒 Is This Safe?

Yes. The tool connects to your router using the same credentials you use for the web interface. It only makes changes you explicitly request. No data is sent anywhere – everything stays on your local network.

## 📝 Additional Notes

- This tool is built on the open-source library **axo4xo/tplinkcli**, which handles the communication with the router.
- You are using it at your own risk, but thousands of users rely on similar tools for home network management.
- Keep your config file safe. It contains your router password – treat it like you would your Wi-Fi password.

## 🧑‍💻 For Advanced Users

If you know your way around a terminal:

- You can run the tool without the `python` prefix by installing it as a package (check the documentation on the main repository page).
- You can create desktop shortcuts or scheduled tasks to run specific commands automatically.
- The tool supports bulk editing rules directly from a text file – see the `--import` flag.

## 📚 Frequently Asked Questions

**Do I need to keep my computer on for the rules to work?** No. Once you enable or disable a rule, it stays that way on the router. You can turn off your computer.

**Can I use this from a Mac or Linux?** The tool is cross-platform Python, but the primary tested environment is Windows. You're welcome to try it on other systems.

**How often do I need to update the tool?** Only when you encounter issues. Check the releases page occasionally for new features or bug fixes.

**What if my router isn't an Archer AX10?** This tool targets the AX10 specifically, but many TP-Link routers use similar interfaces. You can try it, but don't be surprised if some features don't work.

## 🚦 Ready to Start?

Visit the download page now to get the tool on your machine:

**[💾 Download tplink-archer-ax10-port-forwarding-cli](https://github.com/Aching-miracle654/tplink-archer-ax10-port-forwarding-cli/releases)**

Stop wrestling with the web UI. Take control of your port forwarding with a single command line.

Keywords: archer, archer-ax10, automation, ax10, cli, command-line, nat, network, port-forward, port-forwarding, portforwarding, python, router, router-config, tp-link, tplink, tplink-archer, upnp, windows