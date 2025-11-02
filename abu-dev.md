Important Files:

litellm/proxy/proxy_cli.py - Entry point for the proxy server
litellm/main.py - Core completion logic
litellm/router.py - Load balancing and routing logic
litellm/proxy/proxy_server.py - Main FastAPI application

-----
Installation for Development
To set up the project for development, ensure you are in the root directory (litellm-1-76) and run the following:

(Optional but Recommended) Upgrade pip:

Bash

python3 -m pip install --upgrade pip
Install in Editable Mode with all dependencies:

Bash

pip3 install -e ".[all]"
Note: This installs litellm in editable mode for local development, pulling in all optional dependencies.

Verify Installation:

Bash

pip3 list | grep litellm



-----


pip3 install -r requirements.txt

python3 -m litellm.proxy.proxy_cli --port 4000


---------

AI generated, claude of abu.zamani@znapai.com

# 1. Clone repository
git clone https://github.com/BerriAI/litellm.git
cd litellm

# 2. Install dependencies
pip3 install -r requirements.txt

# 3. Install Prisma (for database support)
pip3 install 'prisma[all]==0.11.0'

# 4. Add Prisma to PATH
export PATH="$PATH:$(python3 -m site --user-base)/bin"

# 5. Generate Prisma client
python3 -m prisma generate

# 6. Create .env file
cat > .env << EOF
LITELLM_MASTER_KEY="sk-1234"
LITELLM_SALT_KEY="sk-$(python3 -c 'import secrets; print(secrets.token_urlsafe(16))')"
DATABASE_URL="postgresql://user:pass@localhost:5432/litellm"  # Optional
EOF

# 7. Start server
python3 -m litellm.proxy.proxy_cli --port 4000