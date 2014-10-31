I was getting `~RVM_PROJECT_PATH` in my prompt.

Solution was to edit `./zprezto/modules/prompt/functions/prompt_theme_setup` and change `%~%` to `%1/%`

```
  # Define prompts.
  PROMPT="
${_prompt_steeef_colors[3]}%n%f at ${_prompt_steeef_colors[2]}%m%f in ${_prompt_steeef_colors[5]}%1/%f "'${vcs_info_msg_0_}'"
"'$python_info[virtualenv]'"$ "
  RPROMPT=''
}
```