
# Cross-Chain Voting App

## User-Focused Summary
Cross-Chain Voting App is a decentralized application designed to provide secure and private voting capabilities across multiple blockchain networks. By leveraging the Secret Network, it ensures that votes are confidential and tamper-proof. Users can cast their votes on Polygon, Ethereum (Mainnet and Sepolia), and Scroll networks, while the Secret Network handles the vote encryption and decryption to ensure privacy.

## Investor Pitch
In the modern digital landscape, the need for secure and private voting mechanisms is paramount to ensure fair and transparent elections and decision-making processes. The Cross-Chain Voting App addresses this need by integrating with multiple blockchain networks to provide a versatile and secure voting platform. With the Secret Network's privacy-preserving features, this application ensures that votes remain confidential, mitigating the risks of voter coercion and bribery. This positions our app as a crucial tool for any organization, community, or governance system that requires secure and private voting mechanisms.

## Development Deep Dive

### Project Structure
The project is organized into several directories and files:

```
myprojectname/
├── Cargo.lock
├── Cargo.toml
├── README.md
├── src/
│   ├── contract.rs
│   ├── lib.rs
│   ├── msg.rs
│   ├── state.rs
├── frontend/
│   ├── index.html
│   ├── app.js
│   ├── styles.css
```

### Smart Contract (Secret Network)

#### `contract.rs`
The main contract file where the voting logic is implemented. Key functionalities include:

- **init**: Initializes the voting contract with the list of candidates and the voting period.
- **handle**: Manages vote casting by users. Each vote is encrypted to ensure privacy.
- **query**: Allows querying of the vote counts and other contract states, ensuring that results can only be decrypted and viewed after the voting period ends.

#### `msg.rs`
Defines the messages used for initialization (`InitMsg`), handling (`HandleMsg`), and querying (`QueryMsg`).

#### `state.rs`
Defines the `State` struct used for storing the contract data, including the list of candidates, vote counts, and voter addresses.

### Cross-Chain Integration

#### Polygon, Ethereum (Mainnet and Sepolia), and Scroll Networks
Smart contracts on these networks interact with the Secret Network contract to submit and retrieve encrypted votes. The cross-chain communication is facilitated through relayers and oracles that ensure data integrity and synchronization across networks.

### Frontend Application
The frontend is built using HTML, JavaScript, and CSS to provide a user-friendly interface for casting votes and viewing results.

#### `index.html`
The main HTML file that structures the frontend application.

#### `app.js`
Handles the frontend logic, including user interactions, form submissions, and blockchain interactions using Web3.js and SecretJS.

#### `styles.css`
Provides the styling for the frontend application.

### Development Process
1. **Generate the Secret Contract Project**
    ```sh
    cargo generate --git https://github.com/enigmampc/secret-template --name votingapp
    cd votingapp
    ```

2. **Compile the Contract**
    ```sh
    npm i -g wasm-opt
    make
    ```

3. **Deploy on Secret Network Testnet**
    ```sh
    secretcli tx compute store contract.wasm.gz --from <your account alias> -y --gas 1000000 --gas-prices=1.0uscrt
    secretcli q tx <txhash>
    ```

4. **Instantiate the Contract**
    ```sh
    INIT='{"candidates": ["Alice", "Bob", "Charlie"], "voting_period": 604800}'
    CODE_ID=<your_code_id>
    secretcli tx compute instantiate $CODE_ID "$INIT" --from <your account alias> --label "voting app" -y
    secretcli query compute list-contract-by-code $CODE_ID
    ```

5. **Frontend Development**
    - Connect the frontend to the Secret Network using SecretJS.
    - Implement voting functionality to interact with the Secret contract.
    - Ensure cross-chain communication with the other blockchain networks.

6. **Testing and Deployment**
    - Thoroughly test the application on testnets (Polygon, Sepolia, Scroll).
    - Deploy the final version on the mainnets once testing is successful.

## Usage Instructions
1. Clone the repository:
    ```sh
    git clone <repository_url>
    cd myprojectname
    ```

2. Install dependencies and compile the contract:
    ```sh
    npm install
    make
    ```

3. Deploy and instantiate the contract on the Secret Network.

4. Start the frontend server:
    ```sh
    cd frontend
    npm start
    ```

5. Open the frontend application in your browser and interact with the voting app.

## Conclusion
The Cross-Chain Voting App leverages the strengths of multiple blockchain networks to provide a secure and private voting platform. By utilizing the Secret Network's privacy-preserving features, we ensure that votes remain confidential, addressing critical challenges in digital voting systems and opening new possibilities for secure, decentralized governance.







# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
