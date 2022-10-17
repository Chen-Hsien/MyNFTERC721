# MyNFTERC721A
721A 相較721較省GAS


ERC721合約Function與ERC20有類似的function名稱, 但其中功能會針對NFT進行調整.  
共有 3個Tokne 資訊view function name, symbol, decimals .  
更多的功能型Function totalSupply, tokenByIndex, tokenOfOwenerByIndex, balanceOf, ownerOf, safeTransferFrom, transferFrom, approve, setApprovalForAll, getApproved, isApprovedForAll, tokenURI, Transfer, Approval, ApprovalForAll.  

safeTransferFrom -> 會檢查賺入的地址是否有轉出的function, 避免NFT卡在裡面.  
tokenURI -> 重要會放入Token的相關參數
