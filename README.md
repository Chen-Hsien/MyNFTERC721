# MyNFTERC721A
721A 相較721較省GAS


ERC721合約Function與ERC20有類似的function名稱, 但其中功能會針對NFT進行調整.  
共有 3個Tokne 資訊view function name, symbol, decimals .  
更多的功能型Function totalSupply, tokenByIndex, tokenOfOwenerByIndex, balanceOf, ownerOf, safeTransferFrom, transferFrom, approve, setApprovalForAll, getApproved, isApprovedForAll, tokenURI, Transfer, Approval, ApprovalForAll.  

safeTransferFrom -> 會檢查賺入的地址是否有轉出的function, 避免NFT卡在裡面.  
tokenURI -> 重要會放入Token的相關參數

練習中將mint寫為一個function
```Solidity
    function mint(address to, uint quantity) external{
        _mint(to, quantity);
    }
```
原始baseURI為回傳一個空字串, 無法對其進行賦值
```Solidity
    function _baseURI() internal view virtual returns (string memory) {
        return baseURI_;
    }

    string baseURI_;

    function setBaseURI(string memory _str) external{
        baseURI_ = _str;
    }
    ```
       
 調整好後，部署到測試網上，因為在constructor就設mint五個出來, try一下tokenURI是否會報錯
 <img width="285" alt="image" src="https://user-images.githubusercontent.com/24216536/196143592-b8199ab4-3c8f-4ef7-8a93-6efb92b9055d.png">.  
 下一步要調整baseURI, 要使用IPFS上傳圖片, 以及metadata, 這邊使用pinata平台.  
 
 這邊圖片使用最近很紅的AI Dalle-2 來生成吧~~~, 給他一串描述的內容, 就會幫你畫出對應圖片嚕, 這邊生成五張！  
 <img width="221" alt="image" src="https://user-images.githubusercontent.com/24216536/196151323-ca5295b0-bf3c-40b6-85b5-d7c64be15bc9.png">
 <img width="221" alt="image" src="https://user-images.githubusercontent.com/24216536/196151280-980700b0-d61e-4ddb-957c-747bbfe7381c.png">.  
 
 回到pinata將五張png上傳上去, 第二張圖提供的URI就是我們等一下metadata要串的圖片網址!!   
<img width="1160" alt="image" src="https://user-images.githubusercontent.com/24216536/196151633-15617702-c6db-49b0-ae81-71db2093cd20.png">
<img width="1160" alt="image" src="https://user-images.githubusercontent.com/24216536/196151680-fbf984a5-6939-403a-a291-d7ff02525ea0.png">.  

 製作對應的MetaData, 內容為{"name":" #0","image":""}同樣進行上傳.  
<img width="1160" alt="image" src="https://user-images.githubusercontent.com/24216536/196153126-4cc36f39-d6b4-4e10-984a-472198f57811.png">.  

接著就可以去Remix setBaseURI進行設定我們token對應的metaData~~~並利用tokenURI可以確認0~5號NFT對應的metadata是不是有正確設定
<img width="288" alt="image" src="https://user-images.githubusercontent.com/24216536/196153912-78dcb8ab-2256-448b-955c-7ec7cc83bbfc.png">
<img width="288" alt="image" src="https://user-images.githubusercontent.com/24216536/196153993-3041cc10-b00e-4edc-bb14-c95e226a4c8c.png">   

進到testnet.opensea 就可以準備重新整理, 看到我們的NFT了   
<img width="288" alt="image" src="https://user-images.githubusercontent.com/24216536/196153912-78dcb8ab-2256-448b-955c-7ec7cc83bbfc.png">   
<img width="1446" alt="image" src="https://user-images.githubusercontent.com/24216536/196154815-96d08727-1b80-4ae4-847b-c61ab1cc3eaf.png">   

在Detail內也可以看到[contract Address](https://goerli.etherscan.io/address/0x15ef1c3a8f91d6cd9042f1fdac148777fb9ab171)
這邊來進行Verify Contract。 
<img width="1446" alt="image" src="https://user-images.githubusercontent.com/24216536/196155376-489fc4bf-9cb9-4b6b-9fa2-f10fab3962ed.png">   
成功!看到綠勾勾了, 就可以在EtherScan進行合約的互動
<img width="1446" alt="image" src="https://user-images.githubusercontent.com/24216536/196155772-afa4d20a-4fca-4b7a-9246-cce38c31b148.png">   
<img width="1446" alt="image" src="https://user-images.githubusercontent.com/24216536/196155940-044685c5-05eb-4e8e-a775-cbd1bd23b984.png">






 
 
 
 
 
