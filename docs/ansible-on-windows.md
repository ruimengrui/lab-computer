# Running ansible playbooks on Windows

Jeff Geerling, an authoritative source on all things "ansible", has a
blog post about running ansible on Windows 10.

[www.jeffgeerling.com/blog/2017/using-ansible-through-windows-10s-subsystem-linux](https://www.jeffgeerling.com/blog/2017/using-ansible-through-windows-10s-subsystem-linux)

The basic steps are:

1. Put the computer in Developer mode.
2. Install the Windows Subsystem for Linux.
3. Install python and required libraries.
4. Install ansible locally, and make sure it is on your path.

```bash
# Install python and required libraries
sudo apt-get -y install python-pip python-dev libffi-dev libssl-dev

# Install ansible locally
pip install ansible --user

# Add the bin containing the ansible programs to the PATH.
echo 'PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc
```

## Running ansible playbooks

We can use an ansible playbook to automate the setting up of a Windows
testing machine. Assuming you have git installed and configured,
you can configure the Windows computer with these two steps:

1. Clone the [lab-computer](https://github.com/lupyanlab/lab-computer)
   repo to the Windows machine
2. Run the ansible playbook.

```bash
git clone https://github.com/lupyanlab/lab-computer.git
cd lab-computer/ansible-playbooks
ansible-playbook setup-windows-testing-computer.yml
```
