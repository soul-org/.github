# SOUL (Saving Oriented Universal Lottery)
   <img src="https://imgur.com/PHipKUY.png" alt="TODO"/>

### Inspiration
The inspiration for SOUL (Saving Oriented Universal Lottery) emerged from the desire to create a financial product that merges the excitement of a lottery with the financial benefits of saving and staking. Traditional lotteries often encourage people to spend money on a chance to win big, but without any returns if they lose. We wanted to flip this concept by integrating lossless saving, ensuring that participants never lose their principal amount while still having a chance to win rewards. This approach aims to provide small-scale crypto holders with an innovative way to grow their assets while engaging in a fun and rewarding experience.

   <img src="https://github.com/soul-org/documents/blob/main/diagrams/SOULMindMap.png" alt="SOUL Mind Map"/>
   <img src="https://github.com/soul-org/documents/blob/main/diagrams/SOULFeatureMindMap.png" alt="SOUL Feature Map"/>

### What It Does
SOUL is a lossless savings product integrated with a lottery mechanism. Here's how it works:

   <img src="https://github.com/soul-org/documents/blob/main/diagrams/SOULUserWorkFlow.png" alt="SOUL Use Cases"/>

1. **Deposits and Pooling**:
    - Participants deposit their cryptocurrency assets into a communal pool. These deposits are then staked to earn rewards over time.

2. **Daily Lottery**:
    - Each day, the staking rewards generated from the pooled assets are collected. A smart contract selects a random winner from the pool of participants, who receives the entire daily reward as their lottery prize.

3. **Lossless Savings**:
    - Unlike traditional lotteries, participants in SOUL do not lose their deposited funds. The principal amount remains safe and can be withdrawn at any time, ensuring that everyone benefits from the staking process regardless of winning the lottery.

### What We Learned
Participating in the development of SOUL has been a tremendous learning experience. Here are some key takeaways:

1. **Smart Contract Development**:
    - We deepened our understanding of writing and deploying smart contracts on the blockchain. Ensuring the security and reliability of these contracts was a top priority, and we learned a great deal about best practices and potential vulnerabilities.

2. **Randomness and Fairness**:
    - Implementing a fair and transparent mechanism for selecting lottery winners required us to delve into Chainlink's VRF (Verifiable Random Function). This integration taught us about creating provably fair and tamper-proof random number generation.

3. **Staking Mechanisms**:
    - We explored various staking mechanisms and their potential returns. Understanding how to efficiently stake assets to maximize rewards was crucial for the sustainability of our lottery system.

4. **User Experience**:
    - We recognized the importance of creating an intuitive and user-friendly interface. Educating users about the benefits and functionality of SOUL was essential to ensure widespread adoption and trust in the platform.

Participating in this hackathon has been an incredible learning experience. Here are some key takeaways:

- **Team Collaboration**: We learned the importance of clear communication and collaboration. Our team used agile methodologies to ensure everyone was on the same page.

- **New Technologies**: We explored several new technologies, including Chainlink CCIP, Functions, Discord Bot, Google Cloud Vision AI.

- **User-Centered Design**: We emphasised user experience by conducting surveys and gathering feedback, which significantly shaped our final product.

- **Time Management**: Working under tight deadlines taught us to prioritise tasks and manage our time efficiently.

## How We Built the Project

Building the SOUL (Saving Oriented Universal Lottery) Platform involved several critical stages, from team formation to deployment. Here's a detailed account of our process:
   <img src="https://github.com/soul-org/documents/blob/main/diagrams/SOULSequenceDiagram.png" alt="SOUL Workflow"/>

### Team Formation and Planning

We began by identifying individuals who shared our project's goals. Our team comprised backend developers, frontend developers, UI/UX designers, and project managers. Once the team was assembled, we applied the Double Diamond design methodology to refine our idea and develop a Minimum Viable Product (MVP). The goals of the MVP were shared with the team during a comprehensive planning session.

### Project Management

To manage our project efficiently, we adopted the SCRUM methodology, conducting daily standups and iterative sprints:

- **GitHub**: Used to host repositories and manage our project via GitHub Projects.

- **CI/CD Pipeline**: Implemented to ensure all changes were tested and bug-free.

- **Communication**: Set up a Discord server for ongoing team communication.

- **Brainstorming and Design**: Utilized Whimsical for brainstorming sessions and creating UML design documents.

### Development Process

#### Initial Setup:

- **Frontend and Backend Scaffolding**: Established the basic structure for both frontend and backend projects.

- **UI/UX Design**: UI/UX designers worked on the frontend design using Figma.

#### Frontend Development:

- **Framework**: Built using Next.js for a robust and scalable frontend.

- **Deployment**: Deployed the frontend on Vercel for continuous integration and delivery.

#### Backend Development:

- **Solidity Contracts**: Developed and scaffolded using Foundry.

- **Base Chain**: Decided to host our Solidity contracts on the Avalanche network.
  
- **Lottery Pool Chains**: Polygon and Avalnche Chains

- **Chainlink Usage**: Implemented for critical functionalities:

    - **Staking Chainlink Function**: We utilized the staking reward API to extract information about the staking APY, validator address and metrics about the staking pool, exposed over REST API.
      > [AnalyticsAPICaller.sol](https://github.com/soul-org/be-contracts/blob/main/src/staking/analytics/AnalyticsAPICaller.sol)
    - **Asset Tranfer Chainlink CCIP**: We implemented Chainlink CCIP contract which are used for sending message cross-chain between polygon and avalanche (base chain) to lottery contract.
      > [TokenTransferor.sol](https://github.com/soul-org/be-contracts/blob/main/src/staking/token/TokenTransferor.sol)
      > [MessageReceiver.sol](https://github.com/soul-org/be-contracts/blob/main/src/staking/messenger/MessageReciever.sol)
      > [MessageSender.sol](https://github.com/soul-org/be-contracts/blob/main/src/staking/messenger/MessageSender.sol)
    - **Lottery Chainlink UpKeep Contract**: A chinlink upkeep enabled Lottery contract to announce winner periodically
      > [Lottery.sol](https://github.com/soul-org/be-contracts/blob/main/src/Lottery/Lottery.sol)
      
 ### Staking Analytics API

   <img src="https://github.com/soul-org/documents/blob/main/diagrams/SOULCrossChainCCIPStaking.png" alt="SOUL Staking Workflow"/>

#### REST APIs:

- **Staking REST API**: This API connects with Staking Reward REST API to query for a specific token for staking metrics, validator addresses. This REST API can be exposed a chainlink function data feed to be used by public.

### Integration and Testing

Once the UI/UX design was complete, we integrated the frontend with the backend services. Comprehensive end-to-end testing was conducted to ensure all components functioned seamlessly together.

### Deployment

With the integration and testing phases complete, we deployed our platform, ensuring that it was accessible and functional for users.

- The backend REST API was deployed on Google Cloud Run on Google Cloud Platform with automated Cloud Build CI/CD pipeline. 

- The solidity contract were deployed using foundry scripts

- The frontend was deployed on vercel.

Challenges Faced
----------------

Throughout the hackathon, we encountered several challenges:

- Scope Creep: Initially, we had a broad vision for the project, which led to potential scope creep. We had to regularly reassess our goals and prioritize features.

- Technical Hurdles: Integrating third-party APIs, such as Google Cloud Vision AI and Discord Bot interface, for event data and ensuring cross-browser compatibility posed significant challenges.

- Team Coordination: Coordinating work across different time zones was tricky, but we overcame this with regular check-ins and flexible work hours. 

- Resource Limitations: Working with limited resources and time forced us to be creative and efficient in our problem-solving approaches.

Despite these challenges, our team's dedication and resilience enabled us to overcome obstacles and deliver a functional and impactful project.

### Accomplishments That We're Proud Of

We are incredibly proud of several key accomplishments that set SOUL apart:

- **Simplicity of the idea**: We think using staking to provide lottery rewards are one of its kind innovation in the space of web3 defi space.
- **Support for the native assets**

These accomplishments reflect our dedication to pioneering solutions and setting new standards in the digital art marketplace.

## Conclusion

SOUL represents a novel fusion of savings and lottery systems, providing a fun yet financially prudent product for crypto holders. Our journey in developing SOUL has equipped us with valuable insights into smart contract development, randomness, staking, and user-centric design. We are excited about the potential of SOUL to revolutionize how people perceive and engage with lotteries and savings in the crypto space.

### What's Next for SOUL (Saving Oriented Universal Lottery) Platform

Our vision for SOUL extends beyond its current capabilities. Moving forward, we aim to further enhance and expand our lottery and staking features. Here are our key focus areas:

1. **Expanding to Other Stakable Chains**:
    - Currently, we support lottery pools on Polygon and Avalanche. Our goal is to extend our lottery pools to include all other stakable chains, broadening the opportunities for our users.

2. **Reducing and Eliminating Fees**:
    - We currently take a percentage of the lottery rewards as a platform fee. To reduce and potentially eliminate these fees, we are exploring the option of running our own staking nodes.
    - Implementing gasless transactions will further help in reducing platform fees.
    - By using our own staking nodes, we can also minimize the lock and unlock periods for staked tokens, providing more flexibility to our users.

3. **Introducing Liquid Staking**:
    - We plan to offer liquid staking options so users' assets are not locked in, allowing them to maintain liquidity.
    - This will also make users eligible for potential airdrops, adding more value to their participation.

4. **Establishing a DAO (Decentralized Autonomous Organization)**:
    - Currently, the SOUL organization decides which lottery pools to host on the platform. With a DAO, we aim to empower our community to make these decisions.
    - The community will be able to elect which lottery pools to host, choose which validators to stake with, and decide on the assets SOUL should support.

By pursuing these goals, we aim to solidify SOUL's position as a leader in lossless saving products, offering unparalleled opportunities and benefits to our users.

Thank you for considering our submission for the Chainlink hackathon. We are eager to continue refining SOUL and exploring new possibilities to enhance its functionality and reach.



