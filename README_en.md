# llm_tokenizers

Language: [English](README_en.md) [中文](README.md)

#### Description  
A collection of tokenizers for various LLMs (Large Language Models).

#### Software Architecture  
Software architecture description.

#### Installation

1. Clone the project to your local machine:
   ```bash
   git clone https://gitee.com/sky_flash/llm_tokenizers.git
   ```


2. Navigate into the project directory:
   ```bash
   cd llm_tokenizers
   ```


3. Install dependencies using pip:
   ```bash
   pip install -r requirements.txt
   ```


#### Package Installation

#### Usage Instructions

1. Install via pip:
   ```bash
   pip install llm_tokenizers
   ```


#### Packaging the Project

1. Make sure you have the build tool installed:
   ```bash
   pip install build
   ```


2. Run the build command from the project root directory:
   ```bash
   python -m build
   ```


   After the build completes, the [.whl](file://D:\git-gitee\llm_tokenizers\dist\llm_tokenizers-0.1.0-py3-none-any.whl) and [.tar.gz](file://D:\git-gitee\llm_tokenizers\dist\llm_tokenizers-0.1.0.tar.gz) files will be saved in the `dist/` directory.

3. Install the built [.whl](file://D:\git-gitee\llm_tokenizers\dist\llm_tokenizers-0.1.0-py3-none-any.whl) file (example using the generated filename):
   ```bash
   pip install dist/llm_tokenizers-0.1.0-py3-none-any.whl
   ```


#### API Usage

You can directly use the `DeepSeekTokenizer` class by importing it as follows:

```python
from llm_tokenizers.deepseek_tokenizer import DeepSeekTokenizer
```


##### 1. Get Tokenizer ID

```python
print(DeepSeekTokenizer.id())  # Output: deepseek
```


> The `id()` method returns the unique identifier of this Tokenizer, which can be used in your program to identify which Tokenizer is currently in use.

---

##### 2. Encode Text to Token IDs

```python
text = "Hello, world!"
token_ids = DeepSeekTokenizer.encode(text)
print(token_ids)  # Output: [List of token IDs]
```


> [encode(text: str) -> List[int]](file://D:\git-gitee\llm_tokenizers\llm_tokenizers\deepseek_tokenizer.py#L25-L26)  
> Encodes the input string text into a list of corresponding token IDs.

---

##### 3. Decode Token IDs to Original Text

```python
decoded_text = DeepSeekTokenizer.decode(token_ids)
print(decoded_text)  # Output: Hello, world!
```


> `decode(data: Union[int, List[int], np.ndarray, torch.Tensor, tf.Tensor]) -> str`  
> Supports multiple input types and returns the decoded string.

---

##### 4. Count Token Length

```python
token_count = DeepSeekTokenizer.tokens_len(text)
print(f"Token count: {token_count}")  # Example Output: Token count: 5
```


> `tokens_len(text: str)`  
> Returns the number of tokens generated from the input text.

---

##### ✅ Full Usage Example

```python
from llm_tokenizers.deepseek_tokenizer import DeepSeekTokenizer

# Get identifier
print("Tokenizer ID:", DeepSeekTokenizer.id())

# Encode text
text = "Hello, deepseek tokenizer!"
token_ids = DeepSeekTokenizer.encode(text)
print("Encoded tokens:", token_ids)

# Decode token
decoded = DeepSeekTokenizer.decode(token_ids)
print("Decoded text:", decoded)

# Count tokens
print("Token count:", DeepSeekTokenizer.tokens_len(text))
```


---

##### 📌 Notes:

- [DeepSeekTokenizer](file://D:\git-gitee\llm_tokenizers\llm_tokenizers\deepseek_tokenizer.py#L10-L34) is a **class-method-driven** utility class. All methods are `@classmethod`, and no instantiation is required.
- The required `transformers` model files should be placed in the `resources/deepseek_tokenizer/` directory.
- If using `np.ndarray`, `torch.Tensor`, or `tf.Tensor` data types, ensure the corresponding libraries (`numpy`, `torch`, `tensorflow`) are installed.

---

#### Command-line Usage

After installing the package (e.g., via [.whl](file://D:\git-gitee\llm_tokenizers\dist\llm_tokenizers-0.1.0-py3-none-any.whl)), you can use the `llm-token` command:

```bash
llm-token [OPTIONS]
```


##### Command-line Arguments

| Option | Long Form | Description | Example |
|--------|-----------|-------------|---------|
| `-t` | `--tokenizer` | Specify the tokenizer type | `llm-token -t deepseek -i "Hello"` |
| `-f` | `--file` | Specify input file path | `llm-token -f ./input.txt` |
| `-u` | `--url` | Specify input URL | `llm-token -u https://example.com/text` |
| `-o` | `--output` | Specify output file path | `llm-token -i "Hello" -o ./output.txt` |
| `-c` | `--count` | Count token length | `llm-token -c -i "Hello world"` |
| `-i` | `--input` | Directly input text content | `llm-token -i "Hello world"` |
| `--read-charset` |  | Specify character set for file reading | `llm-token -f ./input.txt --read-charset gbk` |

##### Usage Examples

1. **Encode text directly**:
   ```bash
   llm-token -i "Hello, world!"
   ```


2. **Count tokens in text**:
   ```bash
   llm-token -c -i "Hello, world!"
   # Example Output: tokens count: 5
   ```


3. **Encode content from a file**:
   ```bash
   llm-token -f ./input.txt
   ```


4. **Encode content from a URL**:
   ```bash
   llm-token -u https://example.com/sample.txt
   ```


5. **Specify tokenizer type**:
   ```bash
   llm-token -t deepseek -i "Hello, world!"
   ```


6. **Output result to a file**:
   ```bash
   llm-token -i "Hello, world!" -o ./encoded_output.txt
   ```


7. **Specify file reading charset**:
   ```bash
   llm-token -f ./chinese_text.txt --read-charset gbk
   ```


##### Priority Rules

When multiple input options are specified, the following priority is used:
1. `-i` / `--input` (Direct text input)
2. `-f` / `--file` (File input)
3. `-u` / `--url` (URL input)

##### Notes

- At least one input method (`-i`, `-f`, or `-u`) must be specified.
- When using the `-c` option, only the token count is output, not the encoded result.
- Output is printed to the console by default. Use `-o` to specify an output file.

---

#### How to Contribute

1. Fork this repository
2. Create a new branch (e.g., `Feat_xxx`)
3. Commit your changes
4. Create a Pull Request

--- 