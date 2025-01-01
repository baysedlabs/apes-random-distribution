# XRPL NFT Redistribution Tool

A Node.js script for redistributing XRP Ledger NFTs from specified accounts to existing holders.

## Overview

This tool helps redistribute NFTs from specified accounts to existing NFT holders based on their current holdings proportion. It's particularly useful for fair NFT redistribution scenarios where tokens need to be reallocated among existing holders.

## Features

- Queries all NFTs for a specific issuer and taxon
- Excludes specified accounts from redistribution
- Proportionally redistributes NFTs based on current holdings
- Generates detailed redistribution statistics
- Saves complete redistribution plan to JSON file
- Includes validation checks and detailed logging

## Prerequisites

- Node.js installed on your system
- XRPL library (`xrpl.js`)

## Installation

1. Clone this repository:


## Configuration

You can configure the tool by modifying the following variables in `distributeAPES.js`:
javascript
// Set your NFT collection details
const ISSUER_ADDRESS = "your_issuer_address_here";
const TAXON = 1; // Set your NFT taxon number
// Specify accounts to redistribute from
const ACCOUNTS_TO_REDISTRIBUTE_FROM = ["account_address_1", "account_address_2"];
// Specify accounts that should not receive redistributed NFTs
const ACCOUNTS_INELIGIBLE_FOR_REDISTRIBUTION = ["ineligible_account_1"];


### Required Configuration:
- `ISSUER_ADDRESS`: The address that issued the NFT collection
- `TAXON`: The taxon number of your NFT collection (usually 0 or 1)
- `ACCOUNTS_TO_REDISTRIBUTE_FROM`: List of accounts holding NFTs to be redistributed
- `ACCOUNTS_INELIGIBLE_FOR_REDISTRIBUTION`: List of accounts that should not receive redistributed NFTs


## Output

The script generates:
- Console output with detailed statistics
- `nft_redistribution_results.json` file containing:
  - Complete redistribution plan
  - NFT assignments
  - Distribution statistics
  - Holder statistics

## Example Output
{
  "totalNFTs": 10064,
  "burnedNFTs": 66,
  "excludedAccountNFTs": 546,
  "uniqueOwners": 1785,
  "redistributionDetails": [
    {
      "owner": "rhsxg4xH8FtYc3eR53XDSjTGfKQsaAGaqm",
      "currentCount": 636,
      "proportion": 0.0691981286040692,
      "additionalNFTs": 38,
      "newTotal": 674,
      "assignedNFTDetails": [
        {
          "nft_id": "00081388A47691FB124F91B5FF0F5246AED2B5275385689F17D087070000226B",
          "uri": "516D5935616D4D356D756932353478635A6B56466F4E4457364A5742354571457A486E4A3850676E4E5858724172"
        },
        {
          "nft_id": "00081388A47691FB124F91B5FF0F5246AED2B5275385689F8173E03B0000079F",
          "uri": "516D54786865716E6A4D5866487278464A73786D516D33654169766B364A79335743485A6F4D7A4B4D7065323672"
        },
        {
          "nft_id": "00081388A47691FB124F91B5FF0F5246AED2B5275385689F9573AB99000014FD",
          "uri": "516D4E54587358574E436D556E427A71385773635247554438547678535137457144774678437759546B6877314B"
        },
        {
          "nft_id": "00081388A47691FB124F91B5FF0F5246AED2B5275385689F53A83E390000079D",
          "uri": "516D4E6735636D6E564E736F4376526233445442694B37634A55674D753542336D3973756756547332474158316A"
        },
      ]
    },
