# Decentralized Web Hosting with IPFS & 4EVERLAND

In this lab, you'll explore decentralized web technologies by setting up a local IPFS node, publishing content to the distributed web, and deploying a static site using 4EVERLAND's automation platform.

---

## Task 1: Local IPFS Node Setup and File Publishing

**Objective**: Run a personal IPFS node using Docker, publish files to the IPFS network, and verify decentralized access through public gateways.

IPFS (InterPlanetary File System) enables decentralized, content-addressed storage that's resilient to single-point failures. Understanding IPFS helps prepare for Web3 development and decentralized application hosting.

1. **Start IPFS container**:

   ```bash
   docker run -d --name ipfs_node \
     -v ipfs_staging:/export \
     -v ipfs_data:/data/ipfs \
     -p 4001:4001 -p 8080:8080 -p 5001:5001 \
     ipfs/kubo:latest
   ```

   - Wait 60 seconds for initialization

2. **Verify node operation**:

   ```bash
   docker exec ipfs_node ipfs swarm peers
   ```

   - Should show connected peers

3. **Add file to IPFS**:

   ```bash
   echo "Hello IPFS Lab" > testfile.txt
   docker cp testfile.txt ipfs_node:/export/
   docker exec ipfs_node ipfs add /export/testfile.txt
   ```

   - Note the generated CID (e.g., QmXgZAUWd8yo4tvjBETqzUy3wLx5YRzuDwUQnBwRGrAmAo)

4. **Access content**:
   - Via local gateway: `http://localhost:8080/ipfs/<CID>`
   - Via public gateways:
     - `https://ipfs.io/ipfs/<CID>`
     - `https://cloudflare-ipfs.com/ipfs/<CID>`
   - *Note: Public access may take 2-5 minutes*
   - Open a browser and access the IPFS web UI:

     ```sh
     http://127.0.0.1:5001/webui/
     ```

   - Share information about connected peers and bandwidth in your report.
   - Provide the hash (CID) and the public gateway URLs used to verify the file on the IPFS gateways.

---

## Task 2: Static Site Deployment with 4EVERLAND

**Objective**: Deploy a website to IPFS using 4EVERLAND's automation platform and manage continuous deployment workflows. 4EVERLAND simplifies deploying and managing websites on decentralized infrastructure, providing CI/CD-like workflows for Web3 hosting with automatic IPFS publishing.

1. **Set up 4EVERLAND project**:
   1. Sign up at [4EVERLAND.org](https://www.4everland.org/) (use GitHub or any wallet  like Metamask auth)
   2. Click "Create New Project" → "Connect GitHub repository"
   3. Select your current repository and branch or any real pet web app/site
   4. Configure build settings for this repo (if you use your own repo adjust configs):
      - Platform: IPFS/Filecoin
      - Framework: Other
      - Publish directory: `/app`
   5. Deploy!

2. **Verify deployment**:
   - In 4EVERLAND dashboard:
     - Note IPFS CID under "Site Info"
     - Access site via *.4everland.app subdomain
   - Verify on public gateway:
     `https://ipfs.io/ipfs/<CID-from-4EVERLAND>`

---

## Submission Guidelines

1. Create `submission10.md` with:

   ```markdown
   ## Task 1 Results
   - IPFS Node Peer Count: [Number from web UI]
   - IPFS Node Bandwidth: [Number from web UI]
   - Test File CID: [Your CID]
   - Public Gateway URL: [link]

   ## Task 2 Results
   - 4EVERLAND Project URL: [your-site.on..4everland.app]
   - GitHub Repository (if you used your own app): [github.com/your/repo]
   - IPFS CID from 4EVERLAND: [CID shown in dashboard]
   ```

2. Include screenshots of:
   - Successful access via local gateway (Task 1)
   - 4EVERLAND deployment dashboard (Task 2)
   - Site accessed through *.on.4EVERLAND.co domain

3. Submit via pull request.

> **Note**: IPFS propagation delays are normal. If public gateways don't work immediately, try on a next day.
